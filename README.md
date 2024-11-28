
# DevOps-Project

# Script to Install Jenkins

This script automates the installation of Java 17 and Jenkins on Debian-based Linux or macOS systems. It first detects the operating system type (Debian or macOS) and installs the appropriate packages using system-specific package managers (apt for Debian and brew for macOS). The script ensures the prerequisites are installed, adds the Jenkins repository (for Debian), and then installs the necessary software. This makes it easier to set up the environment for Jenkins by automating repetitive installation tasks.

![Screenshot from 2024-11-28 23-29-32](https://github.com/user-attachments/assets/8549204b-75ba-470b-907f-1a3757decb88)


# Setup Master-slave architecture

Setting up a node for a master-slave architecture by utilizing the private key, username, and host details from a remote system, and it is capable of executing 5 tasks at a time

![Screenshot from 2024-11-28 23-47-25](https://github.com/user-attachments/assets/c4ba3448-db8a-49ff-a37d-9cec5181ac2b)

![Screenshot from 2024-11-29 00-03-00](https://github.com/user-attachments/assets/b50dfb7d-149e-49df-afee-a721a06b9d3b)

# Setup Role based authorization

Create a role named project_view and give it read permission.

![Screenshot from 2024-11-29 00-05-41](https://github.com/user-attachments/assets/d6f35d8d-e2a5-49bc-a4f1-d0b6b3edd53b)

Create a item role named project_view with pattern of "project.*" and from the job section give it permission of build, configure, read and workspace.

![Screenshot from 2024-11-29 00-07-03](https://github.com/user-attachments/assets/7d7c24d9-4933-44a0-acb7-c211edb0b8b4)

Create a Global roles named project and give it permisson of project_view.

![Screenshot from 2024-11-29 00-08-10](https://github.com/user-attachments/assets/437c8854-16ae-4ed7-9cb6-925c4174746a)

Add user project in item roles, give it the permission of project_view.

![Screenshot from 2024-11-29 00-08-57](https://github.com/user-attachments/assets/0ce972ea-9cdf-476d-857c-36208a5758af)

Login from the project user

![image](https://github.com/user-attachments/assets/eb7f5faa-e112-4c55-a236-45ca81b055f8)

Now,we will see the jobs with the same pattern.

![Screenshot from 2024-11-29 00-11-32](https://github.com/user-attachments/assets/9066342b-f791-48c1-ad78-7245e1e92806)





