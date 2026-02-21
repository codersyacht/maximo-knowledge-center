## SLS Installation

Create project called ibm-sls

```CMD
oc new-project ibm-sls
```
Execute the following:

```CMD
./01-create-ibm-sls-project.sh
```

**Create IBM entitlement key.**

Create [here](https://myibm.ibm.com/products-services/containerlibrary) if you do not have an ibm entitlement key. <br>

Ensure to update the /keyfiles/ibm-entitlement-key with the IBM entitlement key before executing the below command.

Run the following command:

```CMD
./02-ibm-sls-entitlement.sh
```

content:
```CMD
oc create secret docker-registry ibm-entitlement  --docker-server=cp.icr.io --docker-username=cp --docker-password=${ENTITLEDKEY} --namespace=${NAMESPACE}
```

Install OperatorGroup for LicenseService

oc apply -f 03-ibm-sls-operatorgroup.yaml

```YAML
apiVersion: operators.coreos.com/v1
kind: OperatorGroup
metadata:
  name: ibm-sls-operatorgroup
  namespace: ibm-sls
spec:
  targetNamespaces:
    - ibm-sls
  upgradeStrategy: Default
```

Install Subscription to initiate LicenseService operator installation.

```CMD
oc apply -f 04-ibm-sls-subscription.yaml
```

```YAML
apiVersion: operators.coreos.com/v1alpha1
kind: Subscription
metadata:
  name: ibm-sls
  namespace: ibm-sls
spec:
  channel: 3.x
  installPlanApproval: Automatic
  name: ibm-sls
  source: ibm-operator-catalog
  sourceNamespace: openshift-marketplace
  startingCSV: ibm-sls.v3.8.1
```

This would install the following operators in the ibm-sls namespace.
```
NAME                                               AGE
ibm-sls.ibm-sls                                    4m25s
ibm-truststore-mgr.ibm-sls                         4m11s
```

**Mongo Credentials**

Create secret to store mongo credentials.

Execute the following command:
```CMD
./05-ibm-sls-mongo-credentials.sh
```

content:
```
oc create secret generic ibm-sls-mongo-credentials --from-literal=username=admin  --from-literal=password=password -n ibm-sls
```

**Install License Service**

Ensure to replace the ../keyfiles/mongo.crt content with mongo db certificate.

Run the following command to generate the lsl yaml file.

```CMD
./06-generateLicenseService.sh
```

The above will generate a file named 07-ibm-sls.yaml

Run the following command:

```CMD
oc apply -f 07-ibm-sls.yaml
```

Content of 07-ibm-sls.yaml:
```yaml
kind: LicenseService
metadata:
  name: sls
  labels:
    app.kubernetes.io/instance: ibm-sls
    app.kubernetes.io/managed-by: olm
    app.kubernetes.io/name: ibm-sls
  namespace: ibm-sls
spec:
  license:
    accept: true
  reloadCrd:
    fileUpload: 0
  settings:
    auth:
      enforce: true
    compliance:
      enforce: true
    registration:
      open: true
    reporting:
      maxDailyReports: 90
      maxHourlyReports: 24
      maxMonthlyReports: 12
      reportGenerationPeriod: 3600
      samplingPeriod: 900
  domain: maxsystem.dev.fyre.ibm.com
  mongo:
    nodes:
      - host: maxsystem.dev.fyre.ibm.com
        port: 27017
    configDb: admin
    secretName: ibm-sls-mongo-credentials
    authMechanism: DEFAULT
    dbPrefix: ibm-sls_sls_
    retryWrites: true
    certificates:
     - alias: mongodb
       crt: |
          -----BEGIN CERTIFICATE-----
          ...
          -----END CERTIFICATE-----
```

This will create a LicenseService named sls.

**Success Criteria**

```CMD
oc get Licenseservice -n ibm-sls
```
```
NAME   VERSION   STATUS   INITIALIZED            LICENSEID      REGISTRATIONKEY                        AGE
sls    3.12.1    Ready    MissingConfiguration   10005af7ccdd   fbd90118-c812-5fcf-8d2f-1e920fc00061   22m
```
Check that the license service is successfully installed. A pod with the following naming format will be created and in running state. _sls-api-licensing-_. 
```CMD
[admin@maxserver1 03-sls]$ oc get pods -n ibm-sls
```
```CMD
NAME                                                     READY   STATUS      RESTARTS       AGE
ibm-sls-controller-manager-6c9fcd7789-55rtf              1/1     Running     0              154m
ibm-truststore-mgr-controller-manager-5d994fddc5-x44bl   1/1     Running     0              154m
sls-api-licensing-67547cbc57-8qwb6                       1/1     Running     5 (124m ago)   141m
sls-truststore-worker-tdvzd                              0/1     Completed   0              150m
```
A mongo collection named ibm-sls_sls_licensing will be created.
