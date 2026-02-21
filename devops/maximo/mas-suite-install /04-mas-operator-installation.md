## MAS Operator Installation

**Create project**

Create a file named 01-create-ibm-mas-project.sh with the following content:

```
oc new-project mas-max-core
echo "create project mas-max-core executed successfully"
```
Execute the script.
```CMD
./01-create-ibm-mas-project.sh
```

**Create Entitlement Key**

Create secret for entitlement key.

Create a file named 02-ibm-mas-entitlement-key.sh with the following content:
```
export ENTITLEDKEY="$(<../keyfiles/ibm-entitlement-key)"
export NAMESPACE="mas-max-core"
oc create secret docker-registry ibm-entitlement  --docker-server=cp.icr.io --docker-username=cp --docker-password=${ENTITLEDKEY} --namespace=${NAMESPACE}
```

Execute the script.
```CMD
./02-ibm-mas-entitlement-key.sh
```

**Create Operator Group**

Create a file named 03-ibm-mas-operatorgroup.yaml with the following content:

```yaml
apiVersion: operators.coreos.com/v1
kind: OperatorGroup
metadata:
  name: ibm-mas-operatorgroup
  namespace: mas-max-core
spec:
  targetNamespaces:
    - mas-max-core
  upgradeStrategy: Default
```

Execute the following command:
```CMD
oc apply -f 03-ibm-mas-operatorgroup.yaml
```

**Create Subscription**

Create a file named 04-ibm-mas-subscription.yaml with the following content:
```yaml
apiVersion: operators.coreos.com/v1alpha1
kind: Subscription
metadata:
  name: ibm-mas
  namespace: mas-max-core
spec:
  channel: 9.1.x 
  installPlanApproval: Automatic
  name: ibm-mas
  source: ibm-operator-catalog
  sourceNamespace: openshift-marketplace
  startingCSV: ibm-mas.v9.1.0
  config:
    installModeType: OwnNamespace
```

Execute the following command:
```CMD
oc apply -f 04-ibm-mas-subscription.yaml
```

