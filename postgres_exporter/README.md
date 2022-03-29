https://github.com/prometheus-community/postgres_exporter

wget https://github.com/prometheus-community/postgres_exporter/releases/download/v0.10.1/postgres_exporter-0.10.1.linux-amd64.tar.gz

tar -xvzg postgres.....

mv postgres.../ postgres_exporter/

sudo mv postgres_exporter/ /opt/postgres_exporter/

cd /opt/postgres_exporter

sudo cp postgres_exporter /usr/local/bin

sudo vim postgres_exporter.env<br>
DATA_SOURCE_NAME="postgresql://postgres:postgres@10.184.15.215:9114/?sslmode=disable"<br>

sudo useradd -rs /bin/false postgres_exporter

sudo vim /etc/systemd/system/postgres_exporter.service

[Unit]<br>
Description=Prometheus exporter for Postgresql<br>
Wants=network-online.target<br>
After=network-online.target<br>

[Service]<br>
User=postgres_exporter<br>
Group=postgres_exporter<br>
WorkingDirectory=/opt/postgres_exporter<br>
EnvironmentFile=/opt/postgres_exporter/postgres_exporter.env<br>
ExecStart=/usr/local/bin/postgres_exporter --web.listen-address=10.184.15.215:9114 --web.telemetry-path=/metrics<br>
Restart=always<br>

[Install]<br>
WantedBy=multi-user.target<br>

sudo systemctl daemon-reload

sudo systemctl start postgres_exporter

sudo systemctl enable postgres_exporter

sudo systemctl status postgres_exporter
