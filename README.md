# Monitoring Stack with Ansible (Prometheus, Alertmanager, Node Exporter, Grafana)

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

### Inventory Example (`inventory.ini`)
```ini
[all_nodes]
ec2-user@3.250.196.11
ec2-user@54.247.254.171
```

---

## 📂 Project Structure
```
ansible-monitoring/
├── inventory.ini
├── site.yml
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
### Run the playbook:
```bash
ansible-playbook -i inventory.ini site.yml
```

### Verify services are running:
```bash
ss -tulnp | grep -E '9090|9093|9100|3000'
```

Expected output:
```
*:9090 (Prometheus)
*:9093 (Alertmanager)
*:9100 (Node Exporter)
*:3000 (Grafana)
```

---

## ✅ Verification
- Access **Prometheus UI** → `http://<node_ip>:9090`  
- Access **Alertmanager UI** → `http://<node_ip>:9093`  
- Access **Grafana UI** → `http://<node_ip>:3000`  
- Access **Node Exporter metrics** → `http://<node_ip>:9100/metrics`  

---

## 📌 Future Improvements
- Configure **Prometheus targets** dynamically.  
- Set up **Alertmanager notification channels** (Slack, Email, etc.).  
- Import **Grafana dashboards** automatically.  
- Add **TLS/Authentication** for security.  

---

✍️ **Author**: Hesham Mohamed Soliman Elngar  
