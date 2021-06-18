# Use the official lightweight Python image.
# https://hub.docker.com/_/python
FROM python:3.7-slim

ENV APP_HOME /app
WORKDIR $APP_HOME

RUN apt-get update && \
    apt-get install git -y && \
    git clone -b ce-time-fix https://github.com/pwc-labs/kfserving.git && \
    pip install ./kfserving/python/kfserving
# Install production dependencies.
COPY requirements.txt ./
RUN pip install --no-cache-dir -r ./requirements.txt

# Copy local code to container image
COPY model.py  imagenet_classes.txt ./

CMD ["python", "model.py"]