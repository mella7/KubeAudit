# 🚀 KubeAudit

### **ELK Stack and Kubernetes Integration for Enhanced Security**

---

![KubeAudit](https://img.shields.io/badge/Security%20%26%20Compliance-SMSI-blue) ![Kubernetes](https://img.shields.io/badge/Kubernetes-Orchestration-blue) ![Ansible](https://img.shields.io/badge/Automated%20with-Ansible-green)

KubeAudit is a streamlined, SMSI-compliant logging and monitoring platform combining the **ELK Stack** (Elasticsearch, Logstash, and Kibana) with **Kubernetes** orchestration to enhance security and traceability in containerized environments. Ideal for high-compliance and high-security setups, KubeAudit provides a **centralized** solution to monitor, manage, and analyze logs in real-time.

---

## 🌟 Features

- 🔧 **Automated Deployment**: Ansible-driven setup for ELK and Kubernetes.
- 📈 **Centralized Logging**: Aggregates logs from containerized applications for easy analysis.
- 🔍 **Enhanced Traceability**: Complies with Information Security Management System (SMSI) standards.
- 📊 **Scalability**: Uses Kubernetes to manage app scaling and fault tolerance.

## ⚙️ Architecture

The platform consists of:

- **Node 1**: Runs the ELK Stack to collect, process, and visualize logs.
- **Node 2**: Hosts a Dockerized Python Flask app, orchestrated with Kubernetes for traffic handling and scaling.

---

## 🛠️ Setup and Installation

### Prerequisites

- **RHEL 9.4** (or similar Linux OS) on both nodes.
- **Docker** and **Kubernetes** for containerization.
- **Ansible** for automated deployment.
- **VMware** for creating virtual machines.

### Installation Steps

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/KubeAudit.git
   cd KubeAudit
   
2. **Configure Ansible Playbooks**
   - Open the `ansible/inventory` file and add the IP addresses of your nodes:
     ```ini
     [elk_node]
     <ELK_Node_IP>

     [app_node]
     <App_Node_IP>
     ```
   - Customize any necessary variables in the playbooks or variable files to match your specific setup (e.g., Elasticsearch indices, Logstash pipelines, Kubernetes configurations).

3. **Deploy the ELK Stack on Node 1**
   - Run the Ansible playbook for the ELK stack to set up Elasticsearch, Logstash, and Kibana on the ELK node:
     ```bash
     ansible-playbook -i ansible/inventory ansible/elk-playbook.yml
     ```

4. **Deploy the Flask Application on Node 2**
   - Run the Ansible playbook for the Flask application on the app node:
     ```bash
     ansible-playbook -i ansible/inventory ansible/app-playbook.yml
     ```

5. **Verify the Setup**
   - **Kibana Access**: Open your browser and go to `http://<ELK_Node_IP>:5601` to access Kibana and visualize the collected logs.
   - **Kubernetes Monitoring**: Use `kubectl` commands to manage and monitor the Flask application running on Node 2. Example commands:
     ```bash
     kubectl get pods
     kubectl get services
     kubectl logs <pod-name>
     ```

     🎮 Usage
     - Access Logs: View app and system logs in Kibana (IP addresses, login attempts, system events).

     - Monitor App Health: Kubernetes ensures your Flask app is load-balanced and resilient.

     - Traceability: Use ELK’s powerful querying to comply with SMSI guidelines for traceability.

   - **Application Logs**: In Kibana, search and filter logs to view:
     - Visitor IP addresses
     - Usernames for login attempts
     - Application crash logs
     - Kubernetes load balancing and backup events
