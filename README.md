# Splunk Home Lab with BOTSv3 Dataset

This repository documents my Splunk home lab, created on a Windows 10 virtual machine using VirtualBox. In this lab, I used the BOTSv3 (Boss of the SOC v3) dataset, which is designed for practicing threat detection, log analysis, and security monitoring in Splunk. This write-up provides an overview of the environment, the dataset, and example exercises to familiarize myself with Splunk.

---

## Lab Environment

- **Platform**: Windows 10 VM
- **Virtualization Tool**: VirtualBox
- **Splunk Version**: Splunk Enterprise (free trial)
- **Dataset**: BOTSv3 (Boss of the SOC v3)
- **Purpose**: Practice log ingestion, search queries, dashboard creation, and event analysis in Splunk.

---

## Installation Steps

### 1. Set up Windows 10 VM in VirtualBox
1. Download and install [VirtualBox](https://www.virtualbox.org/).
2. Set up a Windows 10 virtual machine and configure necessary resources (e.g., RAM, disk space).
3. Install Splunk on the VM.

### 2. Install Splunk Enterprise
1. Download the Splunk Enterprise installer for Windows.
2. Follow the installation instructions provided by Splunk.
3. Launch Splunk and configure the admin account for login.

### 3. Import BOTSv3 Dataset
The BOTSv3 dataset is designed by Splunk to simulate real-world security events. It includes a range of logs that help simulate attacks and anomalies.

1. Download the BOTSv3 dataset [here](https://github.com/splunk/botsv3).
2. Use the Splunk Data Inputs feature to import the BOTSv3 data. To do this:
   - Unzip the downloaded file using 7-Zip or a similar extraction tool.
   - Move the unzipped folder in the `C:\Program Files\Splunk\etc\apps` directory.
   - Restart Splunk to load the dataset.
3. Start indexing the data to make it searchable in Splunk.

---

## Sample CTF Questions and Answers
### 1. List out the IAM users that accessed an AWS service (successfully or unsuccessfully) in Frothly’s AWS environment?
![Screenshot 2024-11-09 141232](https://github.com/user-attachments/assets/7301df23-959b-4bdc-b9ed-c99da6b78fc4)

### 2. What is the processor number used on the web servers?
![Screenshot 2024-11-09 142402](https://github.com/user-attachments/assets/1a8651a2-2d1d-44e9-8f24-2c90203dfc36)

### 3. Bud accidentally makes an S3 bucket publicly accessible. What is the event ID of the API call that enabled public access?
https://repost.aws/knowledge-center/s3-bucket-public-access
![Screenshot 2024-11-09 143149](https://github.com/user-attachments/assets/945f89fb-25b1-4508-96f7-a83192ef8bba)

### 4. What is the name of the S3 bucket that was made publicly accessible?
![Screenshot 2024-11-09 143541](https://github.com/user-attachments/assets/ce2ff9fa-6c24-43ff-b3de-d6fcfaccb1b5)

### 5.What is the name of the text file that was successfully uploaded into the S3 bucket while it was publicly accessible?
![Screenshot 2024-11-09 144525](https://github.com/user-attachments/assets/7924974d-c686-4eac-b4b7-d4e6ca7165f8)

### 6. Identify the Most Common HTTP Status Codes for Login Attempts
![Screenshot 2024-11-09 151132](https://github.com/user-attachments/assets/b52899aa-5aff-4fd9-9493-4647baf8e3b3)


---

## Summary

This home lab provided an introduction to Splunk and hands-on experience with the BOTSv3 dataset, allowing for practice in areas like log ingestion, search queries, and dashboard creation. The BOTSv3 dataset is a valuable resource for anyone looking to simulate security incidents and gain insights into threat detection.

---

## Future Steps

1. **Explore Advanced Queries**: Experiment with more complex Splunk queries to dive deeper into specific security events.
2. **Add Real-Time Alerts**: Set up real-time alerts for certain events, like multiple failed logins, to simulate an active monitoring environment.
3. **Integrate Additional Data Sources**: Add more datasets or system logs to create a more comprehensive monitoring environment.

---

## Resources

- [VirtualBox](https://www.virtualbox.org/)
- [Splunk Documentation](https://docs.splunk.com/)
- [BOTSv3 Dataset on GitHub](https://github.com/splunk/botsv3)
- [Splunk Security Essentials](https://splunkbase.splunk.com/app/3435/)

---

Feel free to explore this repository and use these examples to build your own Splunk knowledge and skills with threat detection and analysis.




