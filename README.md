
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

Now, we will see the jobs with the same pattern.

![Screenshot from 2024-11-29 00-11-32](https://github.com/user-attachments/assets/9066342b-f791-48c1-ad78-7245e1e92806)

# Create a pipeline to execute a shell script, on git, on scripting task, Monitor disk utlization and send mail if > 80%, Process Management, take inputs, check for errors, cleanup, backup, logging.

The scripts required to execute the pipeline, including `JenkinsFile`, `proc.sh`, `script1.sh`, and `script2.sh`, are available on GitHub.

![Screenshot from 2024-11-29 00-34-00](https://github.com/user-attachments/assets/330c807b-5dc3-482c-a044-3a82441c2be6)

The Jenkins pipeline performs automation in three stages: **Git Checkout** (cloning the repository), **Disk Usage Check** (executing `script1.sh`), and **Process Management** (executing `proc.sh`). It is configured to run hourly and sends failure notifications via email, providing job details and a link to the console output for troubleshooting.

![Screenshot from 2024-11-29 00-35-06](https://github.com/user-attachments/assets/541aecb8-ba6c-4f2c-9758-d80e6551a889)

This Bash script helps monitor system resources by identifying processes with high resource consumption. It leverages `ps aux` to sort and display the top processes using the most CPU and memory. Furthermore, it detects zombie processes (those in the "Z" state) using `awk`, facilitating effective process management and troubleshooting.

![Screenshot from 2024-11-29 00-37-32](https://github.com/user-attachments/assets/5db8d1c1-37c4-4873-aaa7-29ad494fe786)

This Bash script monitors the disk usage of the root directory by usage percentage. If the usage exceeds 80%, it displays a warning message and exits with an error code. Otherwise, it confirms that the usage is within normal limits. This proactive approach helps admin address potential disk space issues.

![Screenshot from 2024-11-29 00-39-17](https://github.com/user-attachments/assets/bc63cf62-cc31-4cb5-9843-761dc9788a0b)

This Bash script automates backups with optional compression. It accepts source and destination directories, validates them, and creates the destination if needed. Backups are timestamped for uniqueness, compressed with the `-c` flag, or copied directly. Logs track operations, and backups older than 7 days are deleted to save space, ensuring efficient and reliable data protection.

![Screenshot from 2024-11-29 00-44-28](https://github.com/user-attachments/assets/90f07910-a54f-4230-9913-22700f7acf02)

# Build Java app and trigger pipeline

This ensures the installation of Java 17 with the specified version.

![Screenshot from 2024-11-29 00-48-03](https://github.com/user-attachments/assets/bb51e413-cd9f-4027-9fc1-d89ac4f7f10e)

This ensures the installation of Maven 3.9.9

![Screenshot from 2024-11-29 00-48-40](https://github.com/user-attachments/assets/b5ede735-9ea0-4231-9179-11cfe802360d)

This Jenkins pipeline automates the build-test-deploy process for a Java project. It checks out the code from a Git repository, builds it using Maven (skipping tests during packaging), and then executes tests with results published via JUnit. The "Deliver" stage runs a deployment script (deliver.sh). The pipeline allows branch selection via parameters and triggers builds on GitHub pushes. Using Maven 3.9.9 and Java 17, it enforces a 10-minute execution timeout. Post-build actions include archiving artifacts, cleaning up the workspace, and logging the pipeline status (success or failure). This workflow ensures efficient, automated, and reproducible builds with integrated testing and deployment.

![Screenshot from 2024-11-29 00-55-59](https://github.com/user-attachments/assets/c100be30-2c7f-4ba6-ba0b-86841f0ece6e)

The Jenkins pipeline now includes the GitHub repository and allows branch selection via a parameter. 

![Screenshot from 2024-11-29 00-57-58](https://github.com/user-attachments/assets/7d5c8417-3417-42e9-8269-2a682275da34)

In the pipeline section, set the definition to **Pipeline script from SCM**, specifying the Git repository and using `*/main` as the branch specifier.

![Screenshot from 2024-11-29 00-58-50](https://github.com/user-attachments/assets/d35f768f-8b7d-4980-bf9f-2d6e5736ad2d)

The script path is specified as `example-app-pipeline/Jenkinsfile`, where the pipeline script is executed from.

![Screenshot from 2024-11-29 00-59-51](https://github.com/user-attachments/assets/c54f2efe-b3da-477a-8bc9-c2e09605e333)











