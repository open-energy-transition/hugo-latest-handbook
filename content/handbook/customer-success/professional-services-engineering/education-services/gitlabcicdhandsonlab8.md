---
title: "GitLab CI/CD - Hands-On Lab: Working with the GitLab Container Registry"
description: "This Hands-On Guide walks you through the lab exercises in the GitLab CI/CD course."
---

> Estimate time to complete: 15 - 20 minutes

> **We are transitioning to the latest version of this course.** If your group URL starts with `https://spt.gitlabtraining.cloud`, please use the [Version 15.x instructions](https://gitlab.com/gitlab-com/content-sites/handbook/-/blob/d14ee71aeac2054c72ce96e8b35ba2511f86a7ca/content/handbook/customer-success/professional-services-engineering/education-services/gitlabcicdhandsonlab8.md).

## Objectives

Docker is a platform commonly used by developers to build container applications. It is possible to generate Docker containers as a part of a CI/CD build process. In this lab, you will learn how to define a `Dockerfile` for your project, and integrate it into your `.gitlab-ci.yml` file.

### Task A: Add a `Dockerfile`

1. Open your **CICD Demo** project from earlier labs.

1. Add a new file to the **CICD Demo** project by selecting **+ > This directory > New file**

1. In the **Filename** field, enter `Dockerfile`

1. Paste the following into the body of the new file.

    ```Dockerfile
    FROM golang:1.11-alpine as builder
    WORKDIR /usr/build
    ADD main.go .
    RUN go build -o app .

    FROM alpine:latest

    WORKDIR /usr/src

    COPY --from=builder /usr/build/app .
    EXPOSE 8080

    CMD ["/usr/src/app"]
    ```

1. In the **Commit message** field, type `Add Dockerfile`, ensure the **Target Branch** is set to `main`, and click **Commit changes**.

### Task B: Define a `build image` Job

1. In the left navigation bar, click **Code > Repository**

1. Open the `.gitlab-ci.yml` file and click **Edit > Edit single file**. Paste the following new job definition at the end of the file.

    ```yml
    build image:
      stage: build
      image: docker:18
      services:
        - docker:18-dind
      variables:
        IMAGE: $CI_REGISTRY_IMAGE/$CI_COMMIT_REF_SLUG:$CI_COMMIT_SHA
      script:
        - docker login -u $CI_REGISTRY_USER -p $CI_REGISTRY_PASSWORD $CI_REGISTRY
        - docker build -t $IMAGE .
        - docker push $IMAGE
    ```

1. In the **Commit message** field, type `Add "build image" job definition`, ensure the **Target Branch** is set to `main`, and click **Commit changes**.

### Task C: Ensure the Pipeline is Running 

1. Go to **Build > Pipelines**. Click the most recent pipeline run.

1. Click the widget for the **build image** job to see its progress. Wait for the job to complete.

1. In the left navigation pane, click **Deploy > Container Registry** and view the container that was just uploaded by the `build image` job.

## Lab Guide Complete

You have completed this lab exercise. You can view the other [lab guides for this course](/handbook/customer-success/professional-services-engineering/education-services/gitlabcicdhandson).

## Suggestions?

If you wish to make a change to the *Hands-On Guide for GitLab CI/CD*, please submit your changes via Merge Request!
