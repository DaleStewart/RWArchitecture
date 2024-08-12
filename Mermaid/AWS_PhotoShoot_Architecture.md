graph TD
A[Flutter Frontend] -->|HTTP/HTTPS| B[Application Load Balancer ALB]
B -->|/api/process-model| C[EKS Cluster]
B -->|/api/images| C

    subgraph "Amazon EKS Cluster"
        C --> D[Django Backend Service]
        D --> E[Docker Container]
        subgraph "Docker Container"
            E --> F[Django App]
            F --> G[views.py]
            F --> H[models.py]
            F --> I[model_processor.py]
        end
        F -->|Store/Retrieve Data| J[(Amazon RDS PostgreSQL)]
        F -->|Store/Retrieve Files| K[Amazon S3]
    end

    D -->|JSON Response| B
    B -->|HTTP/HTTPS| A
