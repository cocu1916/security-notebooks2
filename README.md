# security-notebooks2
This repo's purpose is to build a custom data science image within a docker container.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/cocu1916/security-notebooks2/HEAD)

The built image is [hosted on Docker-Hub](https://hub.docker.com/r/cocu1916/my-datascience-notebook).

## Using this repo
### With `docker`
Build:

```bash
docker build --rm -t jupyter/my-datascience-notebook
```

Run:

```bash
docker run --rm -it -p 8888:8888 jupyter/my-datascience-notebook
```

### With `docker-compose`
Build and run:
```bash
docker-compose up
```

##### Useful docker commands
To push image:

```bash
docker push cocu1916/my-datascience-notebook
```

To re-tag image:

```bash
docker tag jupyter/my-datascience-notebook cocu1916/my-datascience-notebook
```

To test if you can pull image:

```bash
docker pull cocu1916/my-datascience-notebook
```

Write a docker file:

```bash
FROM jupyter/datascience-notebook:2022-01-24
COPY --chown=${NB_UID}:${NB_GID} requirements.txt /tmp/
RUN pip install --quiet --no-cache-dir --requirement /tmp/requirements.txt && \
    fix-permissions "${CONDA_DIR}" && \
   fix-permissions "/home/${NB_USER}"
```   
