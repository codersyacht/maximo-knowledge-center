## IBM Operator Catalog Installation

This project workspace folder is _/home/admin/apps_.

Create the folders folder called _/home/admin/apps/mas-container/01-catalogsource_.

Create a file named 01-ibm-operator-catalogsource.yaml under 01-catalogsource with the following content.

```YAML
apiVersion: operators.coreos.com/v1alpha1
kind: CatalogSource
metadata:
  name: ibm-operator-catalog
  namespace: openshift-marketplace
spec:
  description: Online Catalog Source for IBM Maximo Application Suite
  displayName: IBM Maximo Operators (v9-250624-amd64)
  image: 'icr.io/cpopen/ibm-maximo-operator-catalog:v9-250624-amd64'
  priority: 90
  publisher: IBM
  sourceType: grpc
  updateStrategy:
    registryPoll:
      interval: 45m
```

Exeute the following command:

```CMD
oc apply -f 01-ibm-operator-catalogsource.yaml
```

### Success Criteria

Describe the catalog.
```CMD
oc describe CatalogSource ibm-operator-catalog -n openshift-marketplace
```
Ensure the Last Observed State shows **READY**.

Cross verify by running the following command to see if mas related operators are available for install.

```CMD
oc get PackageManifests --all-namespaces | grep mas
```

```
openshift-marketplace   ibm-mas-arcgis                                        IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas-aibroker                                      IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas                                               IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas-assist                                        IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas-iot                                           IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas-manage                                        IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas-hputilities                                   IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas-optimizer                                     IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas-facilities                                    IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas-visualinspection                              IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas-monitor                                       IBM Maximo Operators (v9-250624-amd64)   3h18m
openshift-marketplace   ibm-mas-predict                                       IBM Maximo Operators (v9-250624-amd64)   3h18m
```
