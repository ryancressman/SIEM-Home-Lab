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

## Basic Splunk Exercises with BOTSv3

Here are some exercises using the BOTSv3 dataset to get hands-on experience with Splunk.

### Exercise 1: Searching for Suspicious Login Activity
This exercise will help practice search queries for identifying potential unauthorized access.

**Query:**
`index=botsv3 sourcetype=access_combined_wcookie action=login status=403`

**Description:**  
This query searches for login attempts with a status of `403` (Forbidden), indicating possible unauthorized access attempts.

---

### Exercise 2: Detecting Failed Login Attempts
Identify accounts with multiple failed login attempts, which may suggest brute-force attacks.

**Query:**
`index=botsv3 sourcetype=access_combined_wcookie action=login status=401 | stats count by user | where count > 10`

**Description:**  
This query retrieves usernames with more than 10 failed login attempts (`status=401`), indicating potential brute-force attack attempts.

---

### Exercise 3: Analyzing Web Activity
Examine web traffic to identify unusual browsing patterns that could indicate data exfiltration or recon activities.

**Query:**
`index=botsv3 sourcetype=access_combined_wcookie | timechart count by http_method`

**Description:**  
This query provides a time chart of web activity based on HTTP methods, which can reveal spikes in specific actions such as `GET` or `POST` requests.

---

### Exercise 4: Identifying Lateral Movement
Lateral movement detection helps to spot attackers moving between systems within the network.

**Query:**
`index=botsv3 sourcetype="WinEventLog
" EventCode=4624 | stats dc(dest) as unique_destinations by src | where unique_destinations > 1`

**Description:**  
This query finds source systems (`src`) with successful logins to multiple destination systems (`dest`), which could indicate lateral movement by an attacker.

---

### Exercise 5: Tracking Privilege Escalation Attempts
Use this query to detect potential privilege escalation based on event codes and user account changes.

**Query:**
`index=botsv3 sourcetype="WinEventLog
" EventCode=4672 | stats count by user`

**Description:**  
This query looks for event code `4672`, which indicates that a user has been assigned special privileges. Monitoring these can help detect unusual privilege escalations.

---

### Exercise 6: Creating a Security Dashboard
Create a Splunk dashboard to visualize the results of the queries above.

1. Go to **Dashboards > Create New Dashboard**.
2. Add panels to the dashboard by saving each of the search queries as individual panels.
3. Configure visualizations for each panel (e.g., bar charts, line charts, etc.) to represent login attempts, failed logins, web activity, and lateral movement.
4. Save the dashboard for continuous monitoring and quick access to security insights.

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




