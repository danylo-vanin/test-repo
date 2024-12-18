# NGINX Docker Image with Build Provenance

This repository contains the configuration files required to build, push, and validate an NGINX Docker image with a simple static page. The image is built using Google Cloud Build and includes build provenance for enhanced security and traceability.

## Repository Overview

### Files

- `cloudbuild.yaml`: Defines the steps for building, pushing, and generating build provenance for the Docker image.
- `Dockerfile`: Specifies the base image and copies the static page to the NGINX document root.
- `index.html`: A simple HTML file served by the NGINX container.

## Prerequisites

1. **Google Cloud Project**: Ensure you have a Google Cloud project set up with billing enabled.
2. **Artifact Registry**: Create an Artifact Registry repository if not already available.
3. **Cloud Build Permissions**: Ensure your service account has the required permissions for Cloud Build and Artifact Registry.
4. **Google Cloud SDK**: Install and configure the `gcloud` CLI.

## Building and Pushing the Image

### Steps

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd <repository-directory>
   ```

2. Trigger the build using the following command:
   ```bash
   gcloud builds submit --config=cloudbuild.yaml .
   ```

3. The image will be built and pushed to the specified Artifact Registry:
   ```
   us-central1-docker.pkg.dev/osdu-deploy-vanin/test-repo/nginx-test:latest
   ```

## Provenance Generation

The build includes provenance generation for the Docker image. This ensures the image's integrity and provides traceability for the build process. The provenance data is stored alongside the image in Artifact Registry.

## Customization

### Modify the Static Page

1. Replace the `index.html` file with your custom content.
2. Update the `Dockerfile` if necessary.

### Change the Target Repository

Update the repository and image name in `cloudbuild.yaml` as needed:
```yaml
us-central1-docker.pkg.dev/<your-project>/<your-repo>/nginx-test:latest
```

## Support

If you encounter any issues or have questions, feel free to create an issue in the repository or contact the maintainer.

## Change trigger 
0

