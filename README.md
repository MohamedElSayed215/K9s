# K9s with K3s

A simple guide to install and use K9s with a K3s Kubernetes cluster.

---

# Requirements

- Linux Machine
- K3s Installed
- Internet Connection

---

# Install K3s

```bash
curl -sfL https://get.k3s.io | sh -
```

Verify installation:

```bash
sudo kubectl get nodes
```

---

# Install K9s

## Method 1 — Using Webi

```bash
curl -sS https://webinstall.dev/k9s | bash
```

Reload shell:

```bash
source ~/.bashrc
```

---

## Method 2 — Manual Installation

Download latest release:

```bash
wget https://github.com/derailed/k9s/releases/latest/download/k9s_Linux_amd64.tar.gz
```

Extract files:

```bash
tar -xvf k9s_Linux_amd64.tar.gz
```

Move binary:

```bash
sudo mv k9s /usr/local/bin/
```

Verify installation:

```bash
k9s version
```

---

# Configure K9s with K3s

Export kubeconfig:

```bash
export KUBECONFIG=/etc/rancher/k3s/k3s.yaml
```

Make it permanent:

```bash
echo 'export KUBECONFIG=/etc/rancher/k3s/k3s.yaml' >> ~/.bashrc

source ~/.bashrc
```

---

# Run K9s

```bash
k9s
```

---

# Useful K9s Commands

| Key | Description |
|------|-------------|
| :pods | Show Pods |
| :svc | Show Services |
| :deploy | Show Deployments |
| l | View Logs |
| s | Open Shell Inside Pod |
| d | Delete Resource |
| ctrl+a | Show All Namespaces |

---

# Troubleshooting

## Permission Issue

```bash
sudo chmod 644 /etc/rancher/k3s/k3s.yaml
```

Or copy kubeconfig locally:

```bash
mkdir -p ~/.kube

sudo cp /etc/rancher/k3s/k3s.yaml ~/.kube/config

sudo chown $USER:$USER ~/.kube/config
```

Then:

```bash
export KUBECONFIG=~/.kube/config
```

---

# References

- https://k9scli.io/
- https://k3s.io/

