# Introduction

This is a sample 12factor application that can be deployed on Kubernetes using Epinio. The 12factor application is a simple ruby web app with pages which explain about the 12 factors/principles to be followed while developing your cloud-native application. 

Note: This is the simplest ruby web app with no complexities. For a more complicated ruby app, you can go to [Ruby App](https://github.com/epinio/example-rails)

# Deploy

## Step 1 - Create a cluster

```bash
k3d cluster create epinio -p 80:80@server[0] -p 443:443@server[0] --k3s-server-arg --disable --k3s-server-arg traefik
```

## Step 2 - Download epinio cli

Find the artifact that matches your OS and architecture by visiting the latest
release here: https://github.com/epinio/epinio/releases

You need to download that binary and put it in your PATH. Something like this
should work on Linux (replace the link with right one for your binary):

```bash
# Download the binary
wget https://github.com/epinio/epinio/releases/download/v0.0.16/epinio-linux-amd64
# Make the binary executable
chmod +x epinio-linux-amd64
# Put epinio in your PATH
mv epinio-linux-amd64 /usr/bin/epinio
# Enable epinio autocompletion
epinio comp bash > comp
source comp
```

## Step 3 - Install epinio

```bash
epinio install
```

## Step 4 - Clone 12factor repo

```bash
git clone https://github.com/epinio/example-12factor.git
cd example-12factor
```

## Step 5 - Push 12factor app

```bash
epinio push -n app1
```

Note: Don't name your app with as `12factor` as `epinio` doesn't accept app names starting with a numeric.

## Step 6 - Visit website

You will recieve a URL at the end of the `push` process. Use that url to access your 12factor app.
