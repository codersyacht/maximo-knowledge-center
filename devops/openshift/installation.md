## Installing OpenShift Local


**1. Create a non-root user account in linux.**

Follow the instruction in the link below:

[Non-root user account](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/system/user-management.md)

Login to the machine as admin.

**2. Update yum**

```CMD
sudo yum update -y
```

```CMD
mkdir -p /home/admin/apps/ocp
```
```CMD
cd  /home/admin/apps/ocp
```

Two files are required to install OpenShift local.
- crc-linux-amd64.tar.xz
- pull-secret.txt

## Download crc-linux-amd64.tar.xz

**Note:**

Due to a recently observed issue in using the latest CRC, recommending to use CRC version 2.54.0. In the latest CRC version Operators are not displayed in the UI under catalog though the catalogs are loaded and operators can be installed. CRC git issue has been raised.

**Download CRC 2.54.0.**

Execute the following command from /home/admin/apps/ocp.

```CMD
wget -O  crc-linux-amd64.tar.xz https://developers.redhat.com/content-gateway/file/pub/openshift-v4/clients/crc/2.54.0/crc-linux-amd64.tar.xz
```

**Download Latest version of CRC.**

Execute the following command from /home/admin/apps/ocp.

```CMD
wget -O  crc-linux-amd64.tar.xz https://developers.redhat.com/content-gateway/rest/mirror/pub/openshift-v4/clients/crc/latest/crc-linux-amd64.tar.xz
 ```

The above command will download crc-linux-amd64.tar.xz.

**3. Download the pull secret.**


- Login or, if not registered, register at the following Red Hat website:  
_https://console.redhat.com/_
- Click "_Red Hat OpenShift_".
- Click on "_Create Cluster_" under _Red Hat OpenShift Container Platform_.
- Under "_Select an OpenShift cluster type to create_" select "_Local_".
- **Note: The following action is already performed in the previous step _Download crc-linux-amd64.tar.xz_.This can be skipped. If the previous step _Download crc-linux-amd64.tar.xz_ was not executed, then download this file manually and move it tho the linux machine along with the pull secret to /home/admin/apps/ocp**
   Choose Linux or the right operating system and click on "Download OpenShift Local".  
- Click on _Copy Pull Secret_. Create a file called pull-secret.txt under /home/admin/apps/ocp and paste the secret into it. Or Get the secret by clicking the "_Download Pull secret_". 
- If you have chosen to download, two files will be downloaded: crc-linux-amd64.tar.xz and pull-secret.txt.
- Move the downloaded files to the Linux server under /home/admin/apps/ocp

**4. Installing OpenShift Local**

Login into the server as admin user (_Direct login, NOT sudo login)_.

Stop Firewall

```CMD
sudo systemctl stop firewalld
```
```CMD
sudo systemctl disable firewalld
```
Extract the tar file.
```CMD
tar -xvf crc-linux-amd64.tar.xz
```
Rename the extracted folder to crc.
```CMD
mv crc-linux-2.54.0-amd64 crc
```
Navigate to user home durectory. 
```CMD
cd /home/admin
```
Create a bin directory.
```CMD
mkdir ~/bin
```
Navigate to apps/ocp directory and execute the following command.

```CMD
cd apps/ocp
```
```CMD
cp ./crc/crc ~/bin
```
Export bin folder path.
```CMD
export PATH=$PATH:$HOME/bin
```
```CMD
echo 'export PATH=$PATH:$HOME/bin' >> ~/.bashrc
```
```CMD
crc setup
```

**5. Configuring Code Ready Container.**

Execute the following commands.
```CMD
crc config set cpus 12
```
```CMD
crc config set memory 49152
```
```CMD
crc config set disk-size 500
```
```CMD
crc config set enable-cluster-monitoring true
```
```CMD
crc config set network-mode system
```
```CMD
crc config set pull-secret-file /home/admin/apps/ocp/pull-secret.txt
```
```CMD
crc config set consent-telemetry no
```
**Optional (Not Required)**
```CMD
crc config set skip-check-daemon-systemd-sockets true     # Only if it's required.
```
```CMD
crc config set skip-check-daemon-systemd-unit true        # Only if it's required.
```
**Run Setup**

```CMD
crc setup
```

On successful installation the following message will be displayed.
```
Your system is correctly setup for using CRC. Use 'crc start' to start the instance.
```

**6. Start Code Ready Container.**

Run the following command.
```CMD
crc start
```
While staring please note the following messages.
```
INFO Starting CRC VM for openshift 4.15.12...     
INFO CRC instance is running with IP 192.168.130.11
```
The above means the cluster is accessible on local ip address 192.168.130.11.
On successul start of code ready container, the following message will be displayed.

```
Started the OpenShift cluster.

The server is accessible via web console at:
  https://console-openshift-console.apps-crc.testing

Log in as administrator:
  Username: kubeadmin
  Password: rff2p-pKUA6-CtEZq-QAkjn

Log in as user:
  Username: developer
  Password: developer

Use the 'oc' command line interface:
  $ eval $(crc oc-env)
  $ oc login -u kubeadmin https://api.crc.testing:6443
```

  Refer to /etc/hosts file. Note the following entties.
  
#Added by CRC
192.168.130.11   api.crc.testing canary-openshift-ingress-canary.apps-crc.testing console-openshift-console.apps-crc.testing default-route-openshift-image-registry.apps-crc.testing downloads-openshift-console.apps-crc.testing oauth-openshift.apps-crc.testing

**7. Checking status of Code Ready Container.**

```CMD
crc status
```
```
CRC VM:          Running
OpenShift:       Starting (v4.18.2)
Disk Usage:      27.51GB of 160.5GB (Inside the CRC VM)
Cache Usage:     28.13GB
Cache Directory: /home/admin/.crc/cache
```

**8. Console url.**

```CMD
crc console --url
```
**9. To access oc command.**

To access oc command for OpenShift command execution run the following command.

```CMD
eval $(crc oc-env)
```
**10. Check if pods are running**
```CMD
oc get pod --all-namespaces
```
```
[admin@maxsystem ~]$ oc get pod --all-namespaces
NAMESPACE                                          NAME                                                      READY   STATUS      RESTARTS        AGE
hostpath-provisioner                               csi-hostpathplugin-gxmvz                                  4/4     Running     2 (5m42s ago)   7m42s
openshift-apiserver-operator                       openshift-apiserver-operator-64bbc74764-bds8l             1/1     Running     0               8m25s
openshift-apiserver                                apiserver-68644c65f7-hpkxk                                2/2     Running     0               8m26s
openshift-authentication-operator                  authentication-operator-78fff77bfc-59rvv                  1/1     Running     0               8m25s
openshift-authentication                           oauth-openshift-778f5f9c99-99rdj                          1/1     Running     0               5m33s
openshift-cluster-machine-approver                 machine-approver-7ffc94b44f-xrw2v                         2/2     Running     0               8m26s
openshift-cluster-samples-operator                 cluster-samples-operator-57bd6bc7f4-fxqkq                 2/2     Running     0               8m24s
openshift-cluster-version                          cluster-version-operator-6bb47cdc5b-6f7fx                 1/1     Running     0               8m24s
openshift-config-operator                          openshift-config-operator-547d868bd6-pnqm5                1/1     Running     3 (6m45s ago)   8m24s
openshift-console-operator                         console-operator-7b898b8b56-fj86d                         1/1     Running     0               8m24s
openshift-console                                  console-7647dd6d4d-shdts                                  1/1     Running     0               101s
openshift-console                                  downloads-569f98f7cc-6vwfs                                1/1     Running     5 (4m58s ago)   8m24s
openshift-controller-manager-operator              openshift-controller-manager-operator-56c9c4cfcb-dhgj2    1/1     Running     0               8m24s
openshift-controller-manager                       controller-manager-9d5695dff-dh7hb                        1/1     Running     0               8m24s
openshift-dns-operator                             dns-operator-7cbb898bb6-m22wk                             2/2     Running     0               8m23s
openshift-dns                                      dns-default-j79nc                                         2/2     Running     0               7m42s
..
..
```

## 11. Install & Configure HA Proxy

[Install & Configure HA Proxy](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/system/ha-proxy.md)

In the local machine from where browser is launched, add the following entry. Here, the IP 9.30.188.69 is the actual IP of the linux machine where HAProxy and Openshift is installed.

```
9.30.188.69 api.crc.testing canary-openshift-ingress-canary.apps-crc.testing console-openshift-console.apps-crc.testing default-route-openshift-image-registry.apps-crc.testing downloads-openshift-console.apps-crc.testing oauth-openshift.apps-crc.testing
```


## OpenShift Console.

Access the Openshift hopepage using the following link.

https://console-openshift-console.apps-crc.testing/

uername is kubeadmin. Password is **rff2p-pKUA6-CtEZq-QAkjn** (Received at time of crc start).
