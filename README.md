# Base Docker Images

Dockerfiles for reusable ToastCode base images.

## Images

- `node24-chrome`: Node.js 24.16.0 on Debian Bookworm Slim with pinned Chromium for Puppeteer.
- `node14-npm7-chrome`: legacy Node/npm/Chrome image.

## Publishing

The GitHub Actions workflow at `.github/workflows/publish-docker-image.yml` builds on `ubuntu-latest` and pushes to Docker Hub.

Set these GitHub repository settings before running it:

- Repository variable `DOCKERHUB_USERNAME`: Docker Hub username used for login.
- Repository variable `DOCKERHUB_IMAGE`: Docker Hub image repository, for example `toastcode/base`.
- Repository secret `DOCKERHUB_TOKEN`: Docker Hub access token with push access.

Manual publishing:

1. Open the `Publish Docker image` workflow.
2. Select the image folder.
3. Set the Docker tag, or leave it empty to use the image folder name.
4. Run the workflow.

Default-branch publishing:

- Pushing changes to `node24-chrome/**` on `master` publishes:
  - `docker.io/$DOCKERHUB_IMAGE:node24-chrome`
  - `docker.io/$DOCKERHUB_IMAGE:node24-chrome-sha-<short-sha>`

Pull example:

```sh
docker pull docker.io/$DOCKERHUB_IMAGE:node24-chrome
```
