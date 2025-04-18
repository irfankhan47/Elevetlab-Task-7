# Task 7: Netdata Monitoring on AWS EC2

Objective:
Install Netdata on an AWS EC2 instance using Docker to monitor system performance, including CPU, memory, disk usage, and Docker container metrics.

Tools Used:
Netdata (open-source real-time monitoring tool)
Docker (for containerization)
AWS EC2 (Amazon Linux 2 / Ubuntu instance)

Steps to Set Up:
Launch an EC2 Instance:
Choose Amazon Linux 2 AMI or Ubuntu 20.04
Select t2.micro (Free Tier eligible)
Open port 19999 for Netdata dashboard access
SSH into the instance using a .pem key pair

Install Docker on EC2 Instance:
```
sudo apt update
sudo apt install docker.io -y
sudo usermod -aG docker $USER
```

Docker run
```
docker run -d --name=netdata -p 19999:19999 netdata/netdata
```

Access the Netdata Dashboard: Open your browser and go to:
```
http://<your-ec2-public-ip>:19999
```

Simulate System Stress (Optional):

Install stress tool:

```
sudo apt install stress -y
```

Run stress test:
```
stress --cpu 4 --timeout 30
```

Explore Netdata Logs:

Inside the Docker container:

```
docker exec -it netdata bash
cd /var/log/netdata
cat error.log
```

Metrics Monitored:
CPU Usage
Memory Usage
Disk I/O
Network Traffic
Docker Containers Metrics

Screenshots:
Netdata Dashboard Before Stress Command:

(Include screenshot here)

Netdata Dashboard After Stress Command:

(Include screenshot here)

docker ps Output:

(Include screenshot of docker ps showing Netdata container)

Log Entries After Stress Test:

(Include screenshot of logs if applicable)

Conclusion:
This task demonstrates how to install and use Netdata for system resource monitoring. The stress test showed how Netdata can visualize CPU spikes and trigger alerts in real-time, offering valuable insights into system performance.
