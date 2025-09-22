# Monitoring Stack with Ansible (Prometheus, Alertmanager, Node Exporter, Grafana)

<img width="1400" height="565" alt="image" src="https://github.com/user-attachments/assets/281a7079-03f7-4054-b44f-a28039ed24cc" />

## 📌 Project Overview
This project automates the deployment and configuration of a complete monitoring stack using **Ansible**.  
The monitoring stack includes:  
- **Prometheus** → Metrics collection and monitoring.  
- **Alertmanager** → Handling alerts and notifications.  
- **Node Exporter** → Exporting server metrics (CPU, memory, disk, etc.).  
- **Grafana** → Visualization and dashboards.  

By using Ansible roles, the setup is **automated, repeatable, and scalable** across multiple nodes.

---

## 🚀 Components and Ports
- **Prometheus**: [http://<node_ip>:9090](http://<node_ip>:9090)  
- **Alertmanager**: [http://<node_ip>:9093](http://<node_ip>:9093)  
- **Grafana**: [http://<node_ip>:3000](http://<node_ip>:3000)  
- **Node Exporter**: [http://<node_ip>:9100/metrics](http://<node_ip>:9100/metrics)  

---

## 🖥️ Environment Setup
### Prerequisites
- Linux servers (Ubuntu / Amazon Linux 2).  
- Ansible installed on the control node.  
- SSH access to managed nodes.  

### hosts Example (`inventory.ini`)
```ini
[all_nodes]
<node_ip>   ansible_user=<username>
<node_ip>   ansible_user=<username> 
```

---

## 📂 Project Structure
```
ansible-monitoring/
├── hosts.ini
├── playbook.yml
└── roles/
    ├── prometheus/
    │   └── tasks/main.yml
    ├── alertmanager/
    │   └── tasks/main.yml
    ├── node_exporter/
    │   └── tasks/main.yml
    └── grafana/
        └── tasks/main.yml
```

---

## ▶️ Usage

### create ansible role for each tool:

<img width="954" height="288" alt="Screenshot 2025-09-21 152143" src="https://github.com/user-attachments/assets/2377b53e-da0f-421f-aa93-6b3030dd4246" />

### Run the playbook:
```bash
ansible-playbook -i hosts site.playbook
```
<img width="1621" height="810" alt="Screenshot 2025-09-21 155200" src="https://github.com/user-attachments/assets/1f6b0d45-1fb5-47a5-8d37-53f5bb632129" />
<img width="1108" height="816" alt="Screenshot 2025-09-21 160104" src="https://github.com/user-attachments/assets/8ea4e0c9-b534-43ba-8e0c-63e33f16609f" />


### Verify services are running:
```bash
ss -tulnp | grep -E '9090|9093|9100|3000'
```

Expected output:

<img width="1147" height="123" alt="Screenshot 2025-09-22 172722" src="https://github.com/user-attachments/assets/f6078232-e118-4590-a144-e565872f2a39" />



---

## ✅ Verification

### Verify every service is enabled and running
#### node1
<img width="1607" height="466" alt="Screenshot 2025-09-21 161922" src="https://github.com/user-attachments/assets/e62ef2c5-ef55-42a7-beb4-af7a1b54e7e7" />
<img width="1625" height="483" alt="Screenshot 2025-09-21 162014" src="https://github.com/user-attachments/assets/040cf854-d845-4841-a600-142f8435c521" />
<img width="1621" height="465" alt="Screenshot 2025-09-21 162030" src="https://github.com/user-attachments/assets/eb93e1f0-3dac-45ed-97ab-27fbdc95665a" />
<img width="1625" height="530" alt="Screenshot 2025-09-21 163221" src="https://github.com/user-attachments/assets/54cbd058-a54a-4663-a93f-11a746456f62" />

#### node2
<img width="1639" height="566" alt="Screenshot 2025-09-21 162316" src="https://github.com/user-attachments/assets/cf0ba6ce-fb84-4cec-9eee-55b26f664866" />
<img width="1616" height="563" alt="Screenshot 2025-09-21 162358" src="https://github.com/user-attachments/assets/cd041508-ea98-4def-906c-f6ba102ee00a" />
<img width="1630" height="505" alt="Screenshot 2025-09-21 162339" src="https://github.com/user-attachments/assets/ef73b817-1ffb-4fbc-86ac-7c75eb9c52b1" />
<img width="1440" height="451" alt="image" src="https://github.com/user-attachments/assets/3e30be8e-0967-4289-b91f-ed2e08ce9483" />



- Access **Prometheus UI** → `http://<node_ip>:9090`  
- Access **Alertmanager UI** → `http://<node_ip>:9093`  
- Access **Grafana UI** → `http://<node_ip>:3000`  
- Access **Node Exporter metrics** → `http://<node_ip>:9100/metrics`  

#### node1
<img width="1919" height="1036" alt="Screenshot 2025-09-21 165314" src="https://github.com/user-attachments/assets/2878bcc2-4cce-44b0-943b-f001439ff029" />
<img width="1916" height="971" alt="Screenshot 2025-09-21 165245" src="https://github.com/user-attachments/assets/48511156-613b-40fe-87ee-04797a9148db" />
<img width="1919" height="995" alt="Screenshot 2025-09-21 165258" src="https://github.com/user-attachments/assets/74be13b7-7e00-4b59-aa7e-f593d5ccbb41" />
<img width="1919" height="873" alt="Screenshot 2025-09-21 165713" src="https://github.com/user-attachments/assets/919829c1-f233-45ba-8b38-8406a564a567" />

#### node2
<img width="1919" height="962" alt="Screenshot 2025-09-21 165540" src="https://github.com/user-attachments/assets/e146e699-6483-4bb4-8f20-ad3c76153686" />
<img width="1919" height="971" alt="Screenshot 2025-09-21 165512" src="https://github.com/user-attachments/assets/34c21742-b023-418a-9b2d-d9cce2ff0ccf" />
<img width="1919" height="964" alt="Screenshot 2025-09-21 165529" src="https://github.com/user-attachments/assets/63c96215-1426-4ca7-a1b9-4d145424bd78" />
<img width="1919" height="983" alt="Screenshot 2025-09-21 165501" src="https://github.com/user-attachments/assets/f8fd3bb6-4e3c-4636-9d64-c8651ae932de" />


---

## 📌 Future Improvements
- Configure **Prometheus targets** dynamically.  
- Set up **Alertmanager notification channels** (Slack, Email, etc.).  
- Import **Grafana dashboards** automatically.  

---

✍️ **Author**: Hesham Mohamed Soliman Elngar  
