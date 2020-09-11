# LAB: Google Cloud Fundamentals: Getting Started with App Engine

## Objectives:
In the lab, you will learn how to perform the following tasks
    - Initialize App Engine.
    - Preview an App Engine application running locally in Cloud Shell.
    - Deploy an App Engine application, so that others can reach it.
    - Disable an App Engine application, when you no longer want it to be visible.


## Requirements:
A valid Google Cloud Platform account with credits to consume GCP resources

## Steps:
1.  Initialize App Engine
    1.  Initialize your App Engine app with your project and choose its region
            gcloud app create --project=$DEVSHELL_PROJECT_ID

    2.  Clone the source code repository for a sample application in the hello_world directory:
            git clone https://github.com/GoogleCloudPlatform/python-docs-samples

    3.  Navigate to the source directory:
            cd python-docs-samples/appengine/standard_python3/hello_world

2.  Run Hello World application locally

