# Cloud Run Terraform Setup

This project sets up a Cloud Run service on GCP using Terraform.

## Steps to Deploy

1. Make sure you have the Google Cloud SDK installed and authenticated.
2. Enable the required APIs:
   ```sh
   gcloud services enable run.googleapis.com cloudbuild.googleapis.com artifactregistry.googleapis.com
   ```
3. Build and push the Docker image:
    ```sh
    docker build -t us-central1-docker.pkg.dev/x5-vivid-science-g/my-repo/hello-world:latest .
    gcloud auth configure-docker us-central1-docker.pkg.dev
    docker push us-central1-docker.pkg.dev/x5-vivid-science-g/my-repo/hello-world:latest 
    ```
4. Initialize and apply the Terraform configuration:
    ``` sh terraform init
        terraform apply
    ```
The output will include the URL of your Cloud Run service. 
    ``` sh cloud_run_url = "https://hello-world-rujwahc4iq-uc.a.run.app"