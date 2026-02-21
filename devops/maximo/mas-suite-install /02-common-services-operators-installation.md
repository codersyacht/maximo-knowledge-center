## Common Services Operators Installation

Create a project called ibm-common-services

```CMD
oc new-project ibm-common-services
```

```CMD
./01-create-ibm-common-services-project.sh
```

Install Common Services Operator Group
```YAML
apiVersion: operators.coreos.com/v1alpha2
kind: OperatorGroup
metadata:
  name: ibm-common-services-operatorgroup
  namespace: ibm-common-services
spec:
  targetNamespaces:
  - ibm-common-services
```

```CMD
oc apply -f 02-ibm-common-services-operatorgroup.yaml
```

Install Subscription to initiate common service operator installation.

```YAML
apiVersion: operators.coreos.com/v1alpha1
kind: Subscription
metadata:
  name: ibm-common-service-operator
  namespace: ibm-common-services
spec:
  channel: v3
  installPlanApproval: Automatic
  name: ibm-common-service-operator
  source: ibm-operator-catalog
  sourceNamespace: openshift-marketplace
```

This will install 2 operators.

```CMD
oc get operators -n ibm-common-services
```
```
NAME                                               AGE
ibm-common-service-operator.ibm-common-services    2m54s
ibm-namespace-scope-operator.ibm-common-services   2m15s
ibm-odlm.ibm-common-services                       108s
```
Ensure the status of these operators are successful. This can be viewed in the openshift console's _Installed Operator_ section.

Install OperandRequest

```YAML
apiVersion: operator.ibm.com/v1alpha1
kind: OperandRequest
metadata:
  name: common-service
  namespace: ibm-common-services
spec:
  requests:
    - operands:
        - name: ibm-cert-manager-operator
        - name: ibm-licensing-operator
      registry: common-service
```

```CMD
oc apply -f 04-ibm-cert-manager-operandrequest.yaml
```

This will install the following 2 additional operators.

```
NAME                                               AGE
ibm-cert-manager-operator.ibm-common-services      2m44s
ibm-licensing-operator-app.ibm-common-services     2m44s
```

### Success Criteria

```CMD
[admin@maxserver1 mas-suite-install]$ oc get pods -n ibm-common-services
```
```
NAME                                                    READY   STATUS    RESTARTS   AGE
cert-manager-cainjector-867d59f9fb-b2mpq                1/1     Running   0          5m27s
cert-manager-controller-f57b446b-vb4kq                  1/1     Running   0          5m28s
cert-manager-webhook-57f7d9c76d-khw9q                   1/1     Running   0          5m26s
ibm-cert-manager-operator-b8444d8df-qvqbx               1/1     Running   0          6m32s
ibm-common-service-operator-7755b7c7cc-wcb24            1/1     Running   0          9m22s
ibm-common-service-webhook-6d7598c75-dzntj              1/1     Running   0          8m32s
ibm-licensing-operator-647fc96798-k64mc                 1/1     Running   0          6m35s
ibm-licensing-service-instance-76c57c4dfc-jprj8         0/1     Running   0          63s
ibm-namespace-scope-operator-6d8fc45f44-grl7f           1/1     Running   0          8m45s
operand-deployment-lifecycle-manager-86b7889f88-ckpth   1/1     Running   0          7m36s
secretshare-865b7f7cd5-8xhz9                            1/1     Running   0          8m27s
```
