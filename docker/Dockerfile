FROM python:3.6-slim-buster

RUN apt-get update \
    && apt-get install -yq --no-install-recommends \
    curl \
    ffmpeg \
    nodejs \
    npm \
    sudo \
    && apt-get clean && rm -rf /var/lib/apt/lists/*

RUN python -m pip install -U pip

WORKDIR /src
EXPOSE 8888

COPY requirements.txt requirements.txt
RUN pip install -r requirements.txt

RUN jupyter labextension install @jupyter-widgets/jupyterlab-manager

ENTRYPOINT ["jupyter", "lab", "--no-browser", "--allow-root"]
CMD ["--ip=0.0.0.0", "--port=8888"]
