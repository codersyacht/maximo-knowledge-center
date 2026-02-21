## Maximo Application Suite Core Installation

Create a new folder named _08-masinstall_ under mas-container. Go to the folder.

Create a file named _01-MasInstall.yaml_ with the following content.

```YAML
piVersion: core.mas.ibm.com/v1
kind: Suite
metadata:
  name: max
  labels:
    app.kubernetes.io/instance: ibm-mas
    app.kubernetes.io/managed-by: olm
    app.kubernetes.io/name: ibm-mas
    mas.ibm.com/instanceId: max
  namespace: mas-max-core
spec:
  license:
    accept: true
  domain: maxsystem.dev.fyre.ibm.com
  settings:
    icr:
      cp: cp.icr.io/cp
      cpopen: icr.io/cpopen
```

Execute the following command:
```CMD
oc apply -f 01-MasInstall.yaml
```
Verify the same.

```CMD
oc describe Suite max -n mas-max-core
```

Review the status section.
```
Status:
  Apis:
    Internal:
      URL:  https://internalapi.mas-max-core.svc
  Cert - Manager:
    External:
      Duration:      8760h0m0s
      Name:          mas-max-core-public-issuer
      Renew Before:  720h0m0s
    Internal:
      Duration:      175200h0m0s
      Name:          mas-max-core-internal-issuer
      Renew Before:  2160h0m0s
  Conditions:
    Last Transition Time:  2025-07-04T13:13:39Z
    Message:               Controller updated primary entity manager to supported version (9.1.0)
    Reason:                VersionUpdateCompleted
    Status:                True
    Type:                  ControllerHealth
    Last Transition Time:  2025-07-05T05:01:45Z
    Message:               MAS is ready to use
    Reason:                Ready
    Status:                True
    Type:                  Ready
    Last Transition Time:  2025-07-04T13:52:28Z
    Message:               MongoDB configuration was successfully verified
    Reason:                Ready
    Status:                True
    Type:                  SystemDatabaseReady
    Last Transition Time:  2025-07-04T13:32:27Z
    Message:               CoreIDP truststore ready
    Reason:                Ready
    Status:                True
    Type:                  IDPReady
    Last Transition Time:  2025-07-05T05:01:45Z
    Message:               BasCfg reconciliation is complete
    Reason:                Ready
    Status:                True
    Type:                  BASIntegrationReady
    Last Transition Time:  2025-07-04T14:26:09Z
    Message:               MAS Licensing API endpoint check succeeded
    Reason:                Ready
    Status:                True
    Type:                  SLSIntegrationReady
    Last Transition Time:  2025-07-04T13:25:03Z
    Message:               MAS Routes ready
    Reason:                Ready
    Status:                True
    Type:                  RoutesReady
    Ansible Result:
      Changed:             0
      Completion:          2025-07-05T05:01:39.080574+00:00
      Failures:            0
      Ok:                  23
      Skipped:             18
    Last Transition Time:  2025-07-04T13:48:37Z
    Message:               Awaiting next reconciliation
    Reason:                Successful
    Status:                True
    Type:                  Running
    Last Transition Time:  2025-07-05T05:01:39Z
    Message:               Last reconciliation succeeded
    Reason:                Successful
    Status:                True
    Type:                  Successful
    Last Transition Time:  2025-07-04T13:49:03Z
    Message:               
    Reason:                
    Status:                False
    Type:                  Failure
  Domain:                  maxsystem.dev.fyre.ibm.com
  Keys:
    Jwt:   max-keys-jwt
    Ltpa:  max-keys-ltpa
  Pod Templates:
  Settings:
    Cert Manager:
      Certificates:
        Private Key:
          Size:  2048
    Cors:
      Allow Credentials:  false
      Allowed Headers:
      Allowed Methods:
      Allowed Origins:
      Expose Headers:
      Max Age:  5
    Custom User Data Model:
      Email Types:
        Id:     work
        Value:  Work
        Id:     home
        Value:  Home
      Phone Types:
        Id:     work
        Value:  Work
        Id:     mobile
        Value:  Mobile
    Data Dictionary:
      Catalog:  ibm-operator-catalog
      Channel:  1.1.x
      Pod Templates:
      Strategy:  Automatic
    Icr:
      Cp:      cp.icr.io/cp
      Cpopen:  icr.io/cpopen
    Images:
      Pull Policy:  IfNotPresent
      Registry:     cp.icr.io/cp
    Locale:
      Country:         GB
      Language:        en
    Manual Cert Mgmt:  false
    Qualtrics:
      Enabled:  true
    Rhm:
      Secret Name:  
    Secrets:
      Certificates:
        External:
          max-cert-public
      Images:
        Pull Secret Name:  ibm-entitlement
    Sso:
      Access Token Timeout:           30m
      Allow Custom Cache Key:         false
      Allow Default Sso Cookie Name:  false
      Custom Login Page:              https://auth.maxsystem.dev.fyre.ibm.com/login
      Default IDP:                    local
      Disable Ltpa Cookie:            false
      Idle Timeout:                   1800
      Idp:
        Enabled:                    true
        Visible:                    true
      Idp Session Timeout:          12h
      Refresh Token Timeout:        12h
      Seamless Login:               false
      Sso Cookie Name:              ltpatoken2_max
      Use Only Custom Cookie Name:  true
    Trust Default C As:             true
    User Data Obfuscation:
      Obfuscate Data On Deletion:  false
    User Data Privacy Access:      NO_ACCESS
    User Data Validation:
      Allow Special Chars:  false
    Walkme:                 enabled
  Versions:
    Controller:  9.1.0
    Generation:  1
    Reconciled:  9.1.0
    Supported:
      9.0.0
      9.0.1
      9.0.10
      9.0.11
      9.0.2
      9.0.3
      9.0.5
      9.0.6
      9.0.7
      9.0.8
      9.0.9
      9.1.0
      9.1.0-pre.stable_7051
      9.1.0-pre.stable_7331
      9.1.0-pre.stable_7790
      9.1.0-pre.stable_8193
      9.1.0-pre.stable_9718
```

Execute the following command to check the pods sorted in the order of creation.

```CMD
oc get pods -n mas-max-core --sort-by=.metadata.creationTimestamp
```
```
NAME                                                     READY   STATUS      RESTARTS       AGE
ibm-truststore-mgr-controller-manager-6b7b5895f8-cclw2   1/1     Running     2 (119m ago)   17h
ibm-mas-operator-8676b99dbc-tjjxp                        1/1     Running     1              17h
max-entitymgr-suite-7c986cc66-qnm7z                      1/1     Running     1              17h
max-monagent-mas-97c66cf74-c5mvq                         1/1     Running     1              17h
max-entitymgr-slscfg-6687d9fccb-mvzdw                    1/1     Running     1              17h
max-entitymgr-addons-54d8d886b8-475rg                    1/1     Running     1              17h
max-entitymgr-idpcfg-f8b446c88-sqzgz                     1/1     Running     1              17h
max-entitymgr-watsonstudiocfg-dd7bcb6d7-hq8t4            1/1     Running     1              17h
max-entitymgr-pushnotificationcfg-ccf997858-ljvtb        1/1     Running     1              17h
max-entitymgr-objectstorage-6685d9c65f-t9mst             1/1     Running     1              17h
max-entitymgr-mongocfg-78bcf69cd7-fgx7p                  1/1     Running     1              17h
max-entitymgr-kafkacfg-6877cdd5fc-48vrn                  1/1     Running     1              17h
max-entitymgr-jdbccfg-7d56d4769f-lncwg                   1/1     Running     1              17h
max-entitymgr-coreidp-679cdbbd8f-m6tqc                   1/1     Running     2              17h
max-entitymgr-bascfg-6475bcb57b-hq6x6                    1/1     Running     1              17h
max-entitymgr-scimcfg-6dfdbdf4d8-8vrp8                   1/1     Running     1              17h
max-entitymgr-ws-557c467dfc-57stv                        1/1     Running     1              17h
max-entitymgr-smtpcfg-7c59cb8bbb-88cd7                   1/1     Running     1              17h
max-entitymgr-appcfg-cbfcdc69b-vrncr                     1/1     Running     1              17h
max-ltpakeygenerator-gstv8                               0/1     Completed   0              17h
max-truststore-worker-kgdqj                              0/1     Completed   0              17h
max-coreidp-truststore-worker-298sz                      0/1     Completed   0              17h
max-oidcclientreg-r7twl                                  0/1     Completed   0              17h
max-admin-dashboard-5cb675c7f8-hfgr6                     1/1     Running     2 (120m ago)   17h
max-navigator-7575bc8c95-cdmsn                           1/1     Running     3 (118m ago)   17h
max-homepage-7c5f47fc6f-l68w9                            1/1     Running     3 (118m ago)   17h
max-coreapi-59fc7895cc-hxjtm                             1/1     Running     1              17h
max-coreapi-59fc7895cc-nh4c2                             1/1     Running     1              17h
max-coreapi-59fc7895cc-q4cwx                             1/1     Running     1              17h
max-mobileapi-59d5568b4f-xjrwp                           1/1     Running     2 (120m ago)   17h
max-internalapi-74dc8c59d5-rlr48                         1/1     Running     1              17h
max-catalogmgr-6dbf865657-2vz2k                          1/1     Running     2 (117m ago)   17h
max-catalogapi-788d586465-72xbx                          1/1     Running     1              17h
max-usersync-coordinator-67956c7c4d-62s5x                1/1     Running     1              17h
max-workspace-coordinator-5754766cdc-zn22c               1/1     Running     1              17h
max-groupsync-coordinator-5889cb6d5d-4zxwh               1/1     Running     1              17h
max-coreidp-5d69df9598-g2vnq                             1/1     Running     1              17h
max-coreidp-login-bb8967ffb-pqz29                        1/1     Running     3 (118m ago)   17h
max-licensing-mediator-77dc6d54c6-49dg7                  1/1     Running     2 (115m ago)   17h
max-milestonesapi-5b9c8847c5-ll6tj                       1/1     Running     2 (117m ago)   16h
max-adoptionusageapi-554cd4767b-7v5xs                    1/1     Running     2 (115m ago)   16h
max-usage-hourly-29194930-l9nm2                          0/1     Completed   0              45m
max-accapppoints-29194930-rwq2t                          0/1     Completed   0              45m
max-usage-daily-29194940-dl65v                           0/1     Completed   0              35m
max-licensingsync-29194950-7bjcl                         0/1     Completed   0              25m
max-usage-historical-29194950-cwlbc                      0/1     Completed   0              25m
max-adoptionusage-reporter-29194965-4sb52                0/1     Completed   0              10m
```
