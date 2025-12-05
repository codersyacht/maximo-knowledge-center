## Install Java

Setup directory /home/admin/apps (This is subjective to the user and environment)

Download IBM Java.

_https://developer.ibm.com/languages/java/semeru-runtimes/downloads/_

```CMD
cd /home/admin/apps
```

**Linux**
```CMD
wget -O java.tgz https://github.com/ibmruntimes/semeru17-certified-binaries/releases/download/jdk-17.0.16%2B8_openj9-0.53.0/ibm-semeru-certified-jdk_x64_linux_17.0.16.0.tar.gz
```

**Mac (aarch64)**
```CMD
wget -O java.tgz https://github.com/ibmruntimes/semeru17-binaries/releases/download/jdk-17.0.16%2B8_openj9-0.53.0/ibm-semeru-open-jdk_aarch64_mac_17.0.16_8_openj9-0.53.0.tar.gz
```
```CMD
tar -xvf java.tgz
```
```CMD
rm -rf java.tgz
```
```CMD
mv jdk-17.0.16+8 jdk17
```
```CMD
chmod 755 -R jdk17
```
