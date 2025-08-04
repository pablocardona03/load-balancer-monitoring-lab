# Load-Balanced Web Infrastructure with Monitoring

This project simulates a distributed, scalable web infrastructure using local virtual machines, Dockerized applications, and observability tools. It includes a load balancer (Nginx), multiple Flask-based backend services, and a full monitoring stack with Prometheus and Grafana. The environment is provisioned using Vagrant.

## 🧰 Tech Stack

- **Vagrant** for virtual machine management
- **Nginx** as a reverse proxy/load balancer
- **Docker & Docker Compose** to containerize apps and services
- **Flask** for web servers
- **Artillery** for performance/load testing
- **Prometheus** for metrics collection
- **Grafana** for data visualization
- **UFW (Uncomplicated Firewall)** for basic network security

## 📁 Project Structure

```
project-root/
├── artillery/                         # Load testing configuration (Artillery)
├── nginx/                             # Nginx reverse proxy configuration
├── node_exporter-1.8.0.linux-arm64/   # Prometheus Node Exporter binary
└── prometheus_y_grafana/              # Monitoring stack
    └── project/
        └── prometheus/                # Prometheus configuration files
```

## 🚀 Features

- Multi-VM setup using Vagrant
- Load balancing between two web services
- Metrics exposure from each service for Prometheus
- Grafana dashboard for real-time monitoring
- Load testing via Artillery
- Basic firewall rules using UFW

## 📦 How to Run

### 1. Start Vagrant Machines
```bash
vagrant up
```

### 2. SSH into the Balancer VM
```bash
vagrant ssh balancer
```

### 3. Navigate to the Docker setup and run the stack
```bash
cd /vagrant/monitoring
docker compose up -d
```

### 4. Access Services
- Web App 1: `http://192.168.56.4`
- Web App 2: `http://192.168.56.5`
- Load Balancer: `http://192.168.56.6`
- Grafana Dashboard: `http://192.168.56.6:3000`
- Prometheus: `http://192.168.56.6:9090`

## 📊 Grafana Credentials
- **Username**: admin
- **Password**: admin

## 🛡️ Firewall Rules (UFW)
- Allows HTTP (80), HTTPS (443), and SSH (22)
- Denies all other ports by default

## 🧪 Load Testing with Artillery
```bash
artillery run load-test.yml
```

## 📌 Notes
- Ensure Docker and Vagrant are installed on your host machine.
- Each VM has its own IP configured in the Vagrantfile.

## 📄 License
This project is for educational purposes.