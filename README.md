# grafana-prometheus-project
Grafana + Prometheus for GCP Monitoring

To install Grafana + Prometheus:



To install Node Exporter on Target servers:
sudo useradd node_exporter -s /sbin/nologin

wget https://github.com/prometheus/node_exporter/releases/download/v*/node_exporter-*.*-amd64.tar.gz
tar xvfz node_exporter-*.*-amd64.tar.gz
sudo mv node_exporter-*.*-amd64/node_exporter node_exporter

sudo cp node_exporter /usr/sbin/
sudo mv node_exporter.service /etc/systemd/system/

sudo mkdir -p /etc/sysconfig
sudo touch /etc/sysconfig/node_exporter

sudo systemctl daemon-reload
sudo systemctl enable node_exporter
sudo systemctl start node_exporter

curl http://localhost:9100/metrics
