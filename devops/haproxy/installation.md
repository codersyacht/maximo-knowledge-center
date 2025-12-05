### HA Proxy Installation

```CMD
sudo yum install haproxy
```
The haproxy configuration file is located in /etc/haproxy/haproxy.cfg.

```CMD
sudo vi /etc/haproxy/haproxy.cfg
```

Identify which IP haproxy is required to forward to. 

**For OpeShift**
If the forward is to a locally running opeshift container.

Open /etc/haproxy/haproxy.cfg. 
Make the following entry:

```YAML
frontend  openshift-app-https
    bind *:443
    default_backend openshift-app-https
    mode tcp
    option tcplog
backend openshift-app-https
    balance roundrobin
    mode tcp
    server     openshift  192.168.130.11:443 check
```
**For Minikube**
If the forward is to a locally running Minikube.

```YAML
frontend  omsappserver-oms.minikube
    bind *:443
    default_backend omsappserver-oms.minikube
    mode tcp
    option tcplog
backend omsappserver-oms.minikube
    balance roundrobin
    mode tcp
    server     minikube  192.168.49.2:443 check
```

Restart the haproxy.
```CMD
sudo systemctl stop haproxy.service
```
```CMD
sudo systemctl start haproxy.service
```
```CMD
sudo systemctl status haproxy.service
```
