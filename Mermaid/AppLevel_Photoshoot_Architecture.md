graph TD
A[Django Project]
A --> B[PhotoShoot_Django_App]

    B --> C[models.py]
    B --> D[services.py]
    B --> E[tasks.py]
    B --> F[views.py]
    B --> G[serializers.py]
    B --> H[urls.py]

    C --> I[Model3D]
    C --> J[Screenshot]

    D --> K[ModelProcessingService]
    D --> L[ScreenshotService]

    E --> M[process_model]
    E --> N[generate_screenshots]

    F --> O[ModelViewSet]
    F --> P[ScreenshotViewSet]

    G --> Q[Model3DSerializer]
    G --> R[ScreenshotSerializer]
