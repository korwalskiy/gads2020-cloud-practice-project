# LAB: Google Cloud Fundamentals: Getting Started with Compute Engine

## Objectives:
In the lab, you will learn how to perform the following tasks
    - Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.
    - Create a Compute Engine virtual machine using the gcloud command line interface.
    - Connect between the two instances.

## Requirements:
A valid Google Cloud Platform account with credits to consume GCP resources

## Steps:
1.  Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.

    gcloud compute instances create my-vm-1 \
    --machine-type "n1-standard-1" \
    --image-project "debian-cloud" \
    --image "debian-9-stretch-20200910" \
    --subnet "default" \
    --tags http

    gcloud compute firewall-rules create allow-http-traffic \
    --action=ALLOW \
    --destination=INGRESS \
    --rules=http:80
    --target-tags=http

2.  Create a Compute Engine virtual machine using the gcloud command line interface.

    gcloud config set compute/zone us-central1-b

    gcloud compute instances create my-vm-2 \
    --machine-type "n1-standard-1" \
    --image-project "debian-cloud" \
    --image "debian-9-stretch-20200910" \
    --subnet "default"

3.  Connect between the two instances
    1.  Use the ping command to confirm that my-vm-2 can reach my-vm-1 over the network
        -   Connect to my-vm-2:
                gcloud compute ssh my-vm-2

        -   Ping my-vm-1 from my-vm-2:
                ping -c 5 my-vm-1

        -   Use the ssh command to open a command prompt on my-vm-1 from my-vm-2:
                ssh my-vm-1

        -   At the command prompt on my-vm-1, install the nginx wb server:
                sudo apt-get install nginx-light -y

        -   Use the nano text editor to add a custom message to the home page of the web server:
                sudo nano /var/www/html/index.nginx-debian.html

        -   Add text like this, and replace YOUR_NAME with your name:
                Hi from YOUR_NAME

        -   Write out the file, and confirm that the web server on my-vm-1 is serving your new page:
                curl http://localhost

                The response will be show a preview of the HTML source of the web server's home page including the custom text added

        -   To exit the command prompt on my-vm-1:
                exit

        -   To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, execute this command:
                curl http://my-vm-1

    2.  Now get the external IP address of my-vm-1 instaance:

        gcloud compute instances list

    3.  Paste the copied IP address of my-vm-1 in a new browser tab and hit enter