# Introduction

This is a sample 12factor application that can be deployed on Kubernetes using Epinio. The 12factor application is a simple ruby web app with pages which explain about the 12 factors/principles to be followed while developing your cloud-native application. 

Note: This is the simplest ruby web app with no complexities. For a more complicated ruby app, you can go to [Ruby App](https://github.com/epinio/example-rails)

# Deploy

## Step 1 - Create a cluster

```bash
bash> k3d cluster create epinio -p 80:80 -p 443:443
```

## Step 2 - Download epinio cli

Find the artifact that matches your OS and architecture by visiting the latest
release here: https://github.com/epinio/epinio/releases

You need to download that binary and put it in your PATH. Something like this
should work on Linux (replace the link with right one for your binary):

```bash
# Download the binary
bash> wget https://github.com/epinio/epinio/releases/download/v0.7.1/epinio-linux-x86_64
# Make the binary executable
bash> chmod +x epinio-linux-x86_64
# Put epinio in your PATH
bash> mv epinio-linux-x86_64 /usr/bin/epinio
# Enable epinio autocompletion
bash> epinio completion bash > comp
bash> source comp
```

## Step 3 - Install epinio

Follow the Epinio installation guide [here](https://docs.epinio.io/installation).

## Step 4 - Clone 12factor repo

```bash
git clone https://github.com/epinio/example-12factor.git
cd example-12factor
```

## Step 5 - Push 12factor app

```bash
epinio push -n app1
```

## Step 6 - Visit website

You will recieve a URL at the end of the `push` process. Use that url to access your 12factor app.
