# Docker

## Basic Python Dockerfile

```Docker
FROM python:3.7

WORKDIR /app

COPY requirements.txt ./requirements.txt

RUN pip install -r requirements.txt

COPY ./app.py /app/app.py

CMD ["python", "./app.py"]
```

## Common commands or flags

Buildkit (enable experimental features).
```bash
DOCKER_BUILDKIT=1 docker build ...
```

Build with SSH key. Useful for cloning privte GitHub repository.
```bash
--ssh github_ssh_key=/Users/$USER/.ssh/id_rsa
```

Quickly add AWS credentials in volume.
```bash
-v /Users/$USER/.aws/credentials:/root/.aws/credentials
```

Add environment file.
```bash
--env-file .env
```


