# KinD Installation

**Must Have (Installed and Running) to Run and Use KinD**  
  - Go 1.6+ 
  - Docker

## Single-Node Installation 
### Installation: KinD

**Details**: https://kind.sigs.k8s.io/docs/user/quick-start

**Chosen Method**: Release from Binaries for AMD64 / x86_64
```sh
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.32.0/kind-linux-amd64
chmod +x ./kind
sudo mv ./kind /usr/local/bin/kind
```

### Creation: Cluster
**Using Latest KinD Image**
```sh
kind create cluster --name <name-of-cluster>
kind create cluster --name cka-cluster
```

**Using Specific KinD Image** 
**Details**: https://github.com/kubernetes-sigs/kind/releases
```sh
kind create cluster --image <KinD-node-image> --name <name-of-cluster>
kind create cluster --image kindest/node:v1.36.1@sha256:3489c7674813ba5d8b1a9977baea8a6e553784dab7b84759d1014dbd78f7ebd5 --name cka-cluster-two
```

## Multi-Node Installation 

### Create: YAML Config
To create a multi-node cluster with multiple control plane and multiple worker nodes. E.g. ```config.yaml```
```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4 # depends entirely on official future release
nodes:
- role: control-plane
- role: worker
- role: worker
```

### Run Command: Creates Cluster
```sh
kind create cluster --config <configuration-file> --name <name-of-cluster>
kind create cluster --config config.yaml --name cka-cluster-three
```

### Inspect the Clusters
```sh
kind get clusters
```

## Interaction with Clusters
To interact with the cluster, it is essential to install Kubectl utility on host machine.

**Details**: https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/ (KUBECTL Utility)

### Download: Latest Binary Release
**Chosen Method**: Release from Binaries for AMD64 / x86_64
```sh
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```
### Validate: Latest Binary (Optional)
```sh
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256"
echo "$(cat kubectl.sha256)  kubectl" | sha256sum --check
```
```txt
kubectl: OK
```
### Install: kubectl
```sh
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl
```
If the user don't have root access
```sh
chmod +x kubectl
mkdir -p ~/.local/bin
mv ./kubectl ~/.local/bin/kubectl
```

### Test: Version of kubectl
```sh
kubectl version --client
kubectl version --client --output=yaml
```
