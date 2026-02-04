# Mixologyfy Virtualization Lab (Vagrant)
This project demonstrates how to package and run a Python web application inside a reproducible virtual machine environment using Vagrant and AlmaLinux 9.

The objective was to simulate a real-world DevOps scenario where application dependencies must be bundled to ensure consistent deployment across systems.

## Lab Objective
The purpose of the lab was to gain practical experience in bundling applications with their dependencies and ensuring consistent execution across environments.

## Tech Stack
- Vagrant
- AlmaLinux 9
- Python 3
- Flask
- psycopg (PostgreSQL driver)
- FIGlet
- Shell provisioning

## Features Implemented
### Virtual Machine Configuration
- AlmaLinux 9 base box

Configured with:
- 2 GB RAM
- 2 CPU cores

Custom hostname:
- almalinux9-vm

## Synced Folder
A synced folder was configured to share the app-src directory from host to guest at:

/app

This allowed live editing of the HTML template directly from the host machine.

## Automated Provisioning
A shell provisioner installs all required dependencies during VM startup, including:
- Python 3 + pip
- Flask (v2+)
- requests (v2+)
- psycopg (v3+)
- PostgreSQL libraries
- FIGlet

An environment variable was also configured so the application can locate the Jinja template without modifying source code:

export APP_TEMPLATE_PATH=/app/index.html.jinja

## Networking
Port forwarding was configured to expose the application:

Guest: 1338 → Host: 1337

Access the web app at:

http://localhost:1337

## How to Run
vagrant up
vagrant ssh -c "python3 /app/mixologyfy.py"

## Screenshots
### Application running
![Application Running](images/screenshots/application-running/application-running.png)

### Before HTML modification 
![Before HTML Modification](images/screenshots/before-html-modification/before-html-modification.png)

### After HTML modification 
![After HTML Modification](images/screenshots/after-html-modification/after-html-modification.png)

### Synced folder demonstration
![Synced Folder Demonstration](images/screenshots/synced-folder-demonstration/synced-folder-demonstration.png)

## What This Project Demonstrates
- Infrastructure as Code
- Automated VM provisioning
- Dependency management
- Port forwarding
- Reproducible environments
- Practical virtualization skills

## Disclaimer
The application source code was provided as part of a university lab and is not included in this repository. No secrets or credentials are stored in this repository.

### Author
Maximilian Lajsic

LinkedIn: https://www.linkedin.com/in/maximilian-lajsic-930554168/
