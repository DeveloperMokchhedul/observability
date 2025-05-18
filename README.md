# observability
devops project observability


# Kubernetes Monitoring with Prometheus
Monitoring pod, service, node and etc resource  use prometheus  for this use prometheus+kube-state-matrics+node+cadvisor

# easyly deploy with help

helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install k8s-monitoring prometheus-community/kube-prometheus-stack




##### use for another rule ######

# install node exporter
# For download Node Exporter
wget https://github.com/prometheus/node_exporter/releases/download/v1.3.1/node_exporter-1.3.1.linux-amd64.tar.gz

# For extractall
tar xvf node_exporter-1.3.1.linux-amd64.tar.gz
cd node_exporter-1.3.1.linux-amd64/

# Run Node Exporter
./node_exporter &

# install prometheus

# Download Prometheus
wget https://github.com/prometheus/prometheus/releases/download/v2.33.1/prometheus-2.33.1.linux-amd64.tar.gz

# Extract file

tar xvf prometheus-2.33.1.linux-amd64.tar.gz
cd prometheus-2.33.1.linux-amd64/

# for configaration yml file 
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'node'
    static_configs:
      - targets: ['localhost:9100']  # Node Exporter

  # run prometheus
./prometheus --config.file=prometheus.yml &


# Grafana

# Grafana add repo
sudo apt-get install -y apt-transport-https
sudo apt-get install -y software-properties-common wget
wget -q -O - https://packages.grafana.com/gpg.key | sudo apt-key add -
echo "deb https://packages.grafana.com/oss/deb stable main" | sudo tee -a /etc/apt/sources.list.d/grafana.list

# Grafana install and start
sudo apt-get update
sudo apt-get install grafana
sudo systemctl start grafana-server
sudo systemctl enable grafana-server








