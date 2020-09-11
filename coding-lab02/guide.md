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
    1.  Execute the following command to download and update the packages list.
            sudo apt-get update

    2.  Set up a virtual environment in which you will run your application; this help to isolate package installations from the system.
        First get the package installed. If prompted for confirmation, press Y and then Enter
            sudo apt-get install virtualenv

    4.  Create the virtual enviromen
            virtualenv -p python3 venv

    5.  Activate the virtual environment.
            source venv/bin/activate

    6.  Navigate to your project directory and install dependencies.
            pip install  -r requirements.txt

    7.  Run the application
            python main.py

    8.  In Cloud Shell, click Web preview (Web Preview) then Preview on port 8080 to preview the application

    9.  Press Ctrl+C to abort the local application instance

    10. Verify no instance is running when the command run below returns an empty list
            gcloud app instances list

3.  Deploy and run Hello World on App Engine
    1.  Navigate to the source directory:
            cd ~/python-docs-samples/appengine/standard_python3/hello_world

    2.  Deploy your Hello World application
        If prompted for confirmation, press Y and then Enter
            gcloud app deploy

    3.  Preview deployed application in browser
            gcloud app browse

4.  Disable the application
    1.  Check for application version
            gcloud app versions list

    2.  Stop application
            gcloud app versions stop VERSION_ID
