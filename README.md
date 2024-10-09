


# Vertically Scale an Already Provisioned EC2 Instance without Terminating & Data Loss

## Introduction
This practical demonstrates how to vertically scale an EC2 instance on AWS without terminating it or losing any data. We'll walk through the process of creating an EC2 instance, connecting to it via SSH, installing a web server, and then modifying the instance type without any data loss.

## Steps Overview
1. Create an EC2 instance on AWS.
2. SSH into the instance and install Apache2.
3. Modify the instance type to a larger one (t2.medium).
4. Confirm no data is lost during the process.

---

## Step 1: Create an EC2 Instance

1. Go to the AWS Console and search for **EC2**, then click on it.
2. Create a new EC2 instance with the following configuration:
   - **Name of Instance**: io-ec2-1077
   - **AMI Image**: Ubuntu
   - **Instance Type**: t2.micro
   - **Key Pair**: Create a new key pair or select an existing one (e.g., linuxkey.pem)
   - **Network Settings**: Leave default settings
3. Click on **Launch Instance**.
![Screenshot from 2024-10-09 15-48-33](https://github.com/user-attachments/assets/af50ad60-6c15-4f3f-8c27-2e4a8979eb12)

   



---

## Step 2: SSH into the EC2 Instance

1. Open your Local Terminal and locate your private key file, in this case Downloads folder has the private key file (linuxkey.pem)
2. Now, used this command to SSH to ec2 instance by aws ssh link or you can also
use following command:-
   ```bash
   cd Downloads
   ssh -i “linuxkey.pem” ubuntu@43.204.29.101 ( change the IP to your
   Instance public IP )
![Screenshot from 2024-10-09 15-52-22](https://github.com/user-attachments/assets/64857901-6144-4018-851b-e47523fad26a)

 
3. If not just copy the AWS ssh link
   ![Screenshot from 2024-10-09 15-49-54](https://github.com/user-attachments/assets/c073cfb6-3e21-4e2f-879d-64c134f665a1)

4. Install Apache2 WebServer
    - sudo apt install apache2
      ![server install](https://github.com/user-attachments/assets/0614eadf-9c87-4bf2-ac80-a4e3cb103058)

5. Start the server
   - sudo systemctl start apache2
7. check the status
   -  sudo systemctl status apache2
  ![status](https://github.com/user-attachments/assets/1a2d6f8a-79de-418a-a141-bbb1ef0e9b06)

## Step 4: Modify the Instance Type
- Stop the running instance. In the AWS console, select your instance, click on Instance State, and select Stop Instance.
![stop](https://github.com/user-attachments/assets/eb3cb4ae-22bd-434a-bf7e-af81fb6e4c34)


- After the instance is stopped, go to Actions, select Instance Settings, and then choose Change Instance Type.
![change](https://github.com/user-attachments/assets/3c11164a-03f4-4be0-ae00-efbf24071082)


- In the Instance type dropdown, select t2.medium.
![change2](https://github.com/user-attachments/assets/de213c13-6611-4b5c-8ab8-d02fd0c62653)


- Start the instance again by selecting Instance State and then Start Instance.
![start](https://github.com/user-attachments/assets/7c5357d6-7868-43d5-a126-b65e356fb759)


- After the instance starts, SSH into it again using the command from Step 2.

- Verify that Apache is still running by using:

-  ```bash
   sudo systemctl status apache2

   
- You can see Apache2 is still there, and we do not need to reinstall the server after restarting the instance (no data loss). Also, confirm that the instance type has changed to t2.medium.


# Conclusion
By following these steps, you have successfully scaled your EC2 instance vertically without terminating the instance or losing any data. The web server was maintained, and the instance type was upgraded from t2.micro to t2.medium.
   
   
   

