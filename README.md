# devops-a2-fa23-bai-010

Personal portfolio page for **MUHAMMAD HAMZA IRFAN** (roll number **fa23-bai-010**), built for
Assignment 2 of DevOps for Cloud Computing.

The page is plain HTML and CSS (`index.html`, `style.css`). It is packaged in a
Docker image based on `nginx:alpine`, and a GitHub Actions workflow checks the
page and publishes the image to Docker Hub on every push to `main`.

## Run it locally

```bash
docker build -t hamza74400/devops-a2:manual .
docker run -d -p 8080:80 --name page hamza74400/devops-a2:manual
```

Then open http://localhost:8080. Stop it with `docker rm -f page`.

## CI/CD

`.github/workflows/ci.yml` runs on every push to `main` and on every pull request:

1. Checks the page (files exist, `<title>` present, roll number present, extra section present).
2. Builds the Docker image.
3. Pushes `hamza74400/devops-a2:latest` to Docker Hub, only on `main`.

Docker Hub credentials come from the repository secrets `DOCKERHUB_USERNAME`
and `DOCKERHUB_TOKEN`.
