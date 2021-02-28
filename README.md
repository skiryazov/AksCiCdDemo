# AksCiCdDemo
AKS CI/CD Demo Project with Github Actions

## Purpose
This little sample shows you the simplest possible CI/CD pipeline that takes your code from your repo and, after every commit, builds it and deploys it to Kubernetes.

It's meant to be a kickstart for both people new to CI/CD as well as those coming from another platform, like Jenkins or particularly Azure DevOps (which Github Actions is expected to one day replace).

For comparison with Azure DevOps please check out my other project, which showcases the same functionality on that platform: https://dev.azure.com/FirebrandSprint/_git/KubernetesDevOps

## Contents
The project uses a .NET web app as an example but it works in exactly the same way with other technologies - that's the beauty of containers.

Here are the "interesting" moving parts that make the CI/CD tick:
- [build.yaml](https://github.com/skiryazov/AksCiCdDemo/blob/main/.github/workflows/build.yml) - the file that defines the Github Actions workflow
- [k8s-deployment.yaml](https://github.com/skiryazov/AksCiCdDemo/blob/main/k8s-deployment.yaml) - the kubernetes-native yaml file that provides the input needed to deploy to the platform

That's literally all of it!

## How to run
This example is specific to AKS (Azure Kubernetes Service) and will not work out of the box on other providers. You can adapt it also for other k8s providers but for the version used in the project you'll need:
- An Azure subscription
- ACR (Azure Container Registry) - this can be changed to another container registry with minor changes
  - Azure service principal with permissions to push images  
You'll need the principal password stored as Github Secret and the principal name and AD tenant as ENV variables
  - An ACR user with permissions to pull images  
Username and password stored as secrets
- An AKS cluster
  - Namespace for your workloads

There is a blog post coming soon explaining everything step-by-step.

## Contributing
Feel free to suggest changes, all kinds of contributions welcome, though anything that makes the example significantly more complex should live in a seprate branch.

In particular, a good addition would be splitting the CI/CD workflow in two parts - CI and CD, repsectively, and adding a manual approval step in between.
