graph TD
A[Flutter Frontend] -->|HTTP/HTTPS| B[IBM Cloud Load Balancer]
B --> C[Application Load Balancer ALB]
C -->|/api/process-model| D[Django Backend Service]
C -->|/api/images| D

    subgraph "IBM Cloud Kubernetes Service Cluster"
        C
        D --> E[Docker Container]
        subgraph "Docker Container"
            E --> F[Django App]
            F --> G[views.py]
            F --> H[models.py]
            F --> I[model_processor.py]
            F --> P[Services.py]
            G --> J[process_model View]
            H --> K[Model3D]
            H --> L[GeneratedImage]
            I --> M[ModelProcessor Class]
        end
        F --> N[(PostgreSQL Database)]
        F --> O[IBM Cloud Object Storage]
    end


    D -->|JSON Response| C
    C --> B
    B -->|HTTP/HTTPS| A
