# Task 7: Netdata Monitoring on AWS EC2

Objective:
Install Netdata on an AWS EC2 instance using Docker to monitor system performance, including CPU, memory, disk usage, and Docker container metrics.

Tools Used:
- Netdata (open-source real-time monitoring tool)
- Docker (for containerization)
- AWS EC2 (Amazon Linux 2 / Ubuntu instance)

Steps to Set Up:
- Launch an EC2 Instance:
- Choose Amazon Linux 2 AMI or Ubuntu 20.04
- Select t2.micro (Free Tier eligible)
- Open port 19999 for Netdata dashboard access
- SSH into the instance using a .pem key pair

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

- Metrics Monitored:
- CPU Usage
- Memory Usage
- Disk I/O
- Network Traffic
- Docker Containers Metrics

Screenshots:
Netdata Dashboard Before Stress Command:

![dashbord main](https://github.com/user-attachments/assets/ca26a126-d91f-43fb-b4cb-a5667ffeb42b)

Netdata Dashboard After Stress Command:

![after stress main](https://github.com/user-attachments/assets/523933c0-52e6-46b9-9a4b-15c131eb0efa)

docker ps Output:

![docker ps](https://github.com/user-attachments/assets/edc84707-12af-4990-919e-f8c61bfddca4)

Log Entries After Stress Test:

![logs](https://github.com/user-attachments/assets/bd6fdb6f-46ca-4106-bf3e-dc3438ff47d4)

Conclusion:
This task demonstrates how to install and use Netdata for system resource monitoring. The stress test showed how Netdata can visualize CPU spikes and trigger alerts in real-time, offering valuable insights into system performance.
