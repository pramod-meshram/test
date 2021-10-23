# Arktos deployment with Mizar CNI
### Prepare lab machine
#### The preferred OS is Ubuntu 18.04. For AWS, the recommended instance size is t2.2xlarge and the storage size is 128GB or more.

#### Kernel version is 5.6.0
## Test Steps:
### 1. Check the kernel version:
### Commmand:

```bash

uname -a

```
### Output:
![](images/image17.png)

### Update the kernel to 5.6.0 version

### command

```bash
wget https://raw.githubusercontent.com/CentaurusInfra/mizar/dev-next/kernelupdate.sh


sudo bash kernelupdate.sh
```
### output:
![](images/image19.png)

![](images/image20.png)

![](images/image21.png)

### Clone the Arktos repository and install the required dependencies:

git clone https://github.com/Click2Cloud-Centaurus/arktos.git ~/go/src/k8s.io/arktos

![](images/image23.png)

git checkout default-cni-mizar

sudo bash ./hack/setup-dev-node.sh

![](images/image23.png)

### step 3. Start Arktos cluster(Arktos came up in the 3rd attempt)

### Command:
```bash
./hack/arktos-up.sh

```
### Output

![](images/image8.png)

### Command
``bash
echo export PATH=$PATH:/usr/local/go/bin\ >> ~/.profile

echo cd \$HOME/go/src/k8s.io/arktos >> ~/.profile

source ~/.profile
![](images/image29.png)

### step 3. Start Arktos cluster(Arktos came up in the 3rd attempt)

### Command:
```bash
./hack/arktos-up.sh

```
### Output
![](images/images31.png)

## Check nodes
### Command
```bash
./cluster/kubectl.sh get nodes

```
### Output
![](images/images33.png)

### Deploy Netpods
### Command
```bash
./cluster/kubectl.sh apply -f netpod.yaml
```
### Output
![](images/image89.png)

### Check deployed pods
### Command
```bash
./cluster/kubectl.sh get pods
```
### Output:
![](images/image63.png)

### Check ping deployed pods
### Command
```bash
./cluster/kubectl.sh get pods -o wide
```
### Output:
![](images/images89.png)

### Command
```bash
./cluster/kubectl.sh exec netpod1 -- ping 10.88.0.6

./cluster/kubectl.sh exec netpod1 -- ping 10.88.0.8

./cluster/kubectl.sh exec netpod1 -- ping 10.88.0.7
```
### Output:

![](images/images54.png)

![](images/images96.png)

![](images/images55.png)

# PASSED




