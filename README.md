# Tutorial: Setting up Django for Production on AWS

In this tutorial, we will guide you through the process of setting up a Django app for production on AWS. We will cover how to configure Django's settings for production, create a `requirements.txt` file, and launch an Ubuntu instance on AWS. We will also cover how to connect to the instance using SSH.

## Prerequisites

Before we begin, ensure that you have the following:

- A Django app ready for deployment
- An AWS account

## Step 1: Prepare Django for Production

Before deploying our Django app to a production server, we need to configure Django's settings for production. Here are the key settings you need to configure:

### ALLOWED_HOSTS

Django uses the `ALLOWED_HOSTS` setting to determine which hostnames are allowed to access the application. In production, you should set this to the hostname or IP address of your server. Open your app's `settings.py` file and add the following line:

```
ALLOWED_HOSTS = ['your_server_ip_or_hostname']
```

### STATIC_ROOT

In production, Django's static files should be served by a web server like Nginx or Apache. To do this, we need to configure Django to collect all the static files into a single directory. Open your app's `settings.py` file and add the following line:

```
STATIC_ROOT = os.path.join(BASE_DIR, 'static')
```


## Step 2: Create a `requirements.txt` File

Create a `requirements.txt` file in the root directory of your project. This file should contain a list of all the Python packages your app depends on, including Django.

To generate this file, activate your virtual environment and use the following command:

```
pip freeze > requirements.txt
```

This will create a file called `requirements.txt` that lists all the installed packages in your virtual environment.

## Step 3: Launch an Ubuntu Instance on AWS

Now that we have prepared our Django app for production, let's launch an Ubuntu instance on AWS.

1. Log in to your AWS account and go to the EC2 dashboard.
2. Click "Launch Instance" and select "Ubuntu Server 20.04 LTS (HVM), SSD Volume Type".
3. Choose an instance type that meets your needs (e.g., t2.micro).
4. In the "Configure Instance Details" section, you can leave the default settings or customize them to meet your needs.
5. In the "Add Storage" section, you can leave the default settings or customize them to meet your needs.
6. In the "Add Tags" section, you can leave the default settings or customize them to meet your needs.
7. In the "Configure Security Group" section, click "Add Rule" and add two rules:
    - Type: HTTP, Source: Anywhere
    - Type: HTTPS, Source: Anywhere
8. Review the settings and click "Launch".
9. Select an existing key pair or create a new one.
10. Launch the instance.

## Step 4: Connect to the Instance Using SSH

Now that we have launched an Ubuntu instance on AWS, let's connect to it using SSH.

1. Go to the EC2 dashboard and select your instance.
2. Click "Connect" and copy the SSH command.
3. Open a terminal window and paste the command.
4. Press Enter and you should now be connected to your instance.

## Conclusion

Congratulations! You have successfully prepared your Django app for production and launched an Ubuntu instance on AWS. You can now deploy your Django app to the instance and configure a web server like Nginx or Apache to serve it.

If you need help deploying your Django app with Gunicorn and Nginx, check out this tutorial: [Deploying a Django App with Gunicorn and Nginx](https://github.com/cgarcia156/Tutorial-Deploy-Django-with-Guniforn-Nginx). It provides a step-by-step guide on how to deploy a Django app using Gunicorn and Nginx on Ubuntu.



