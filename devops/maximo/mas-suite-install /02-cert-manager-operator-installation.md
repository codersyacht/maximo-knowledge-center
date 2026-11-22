## Cert Manager Operators Installation

**Note:**
Cert Manager Operator is used in the higher versions on Openshft. This is primarily used in Maximo 9.2 installation. For older versions refer to 
[common service operator installation](https://github.com/codersyacht/maximo-knowledge-center/blob/main/devops/maximo/mas-suite-install%20/02-common-services-operators-installation.md).

Create a project called cert-manager

```CMD
oc new-project cert-manager
```

```CMD
./01-create-cert-manager-project.sh 
```

Install Cert Manager Operator Group
```YAML
apiVersion: operators.coreos.com/v1
kind: OperatorGroup
metadata:
  name: cert-manager-operator-group
  namespace: cert-manager
spec:
  upgradeStrategy: Default
  targetNamespaces:
    - cert-manager
```

```CMD
oc apply -f 02-cert-manager-operatorgroup.yaml 
```

Install Subscription to initiate Cert Manager operator installation.

```YAML
apiVersion: operators.coreos.com/v1alpha1
kind: Subscription
metadata:
  name: openshift-cert-manager-operator
  namespace: cert-manager
spec:
  channel: stable-v1
  installPlanApproval: Automatic
  name: openshift-cert-manager-operator
  source: redhat-operators
  sourceNamespace: openshift-marketplace
```

This will install 2 operators.

```CMD
oc get operators -n cert-manager
```
```
NAME                                              AGE
openshift-cert-manager-operator.cert-manager      2d23h
```

Ensure the status of these operators are successful. This can be viewed in the openshift console's _Installed Operator_ section.


### Success Criteria

```CMD
[admin@maxserver1 mas-suite-install]$ oc get pods -n cert-manager
```
```
NAME                                                    READY   STATUS    RESTARTS   AGE
cert-manager-597b95cb84-md79m                               1/1     Running   12 (13m ago)   2d23h
cert-manager-cainjector-5c57bbd4fc-x6dfm                    1/1     Running   4              2d23h
cert-manager-operator-controller-manager-7cd865d946-t62z5   1/1     Running   3              2d23h
cert-manager-webhook-5dbbbf75cc-z8thn                       1/1     Running   11 (15m ago)   2d23h
```
