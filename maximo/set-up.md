# Initiatization Steps

### Author: Jawahar

## Change maximo user

Follow the instruction [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/maximo/security/change-password.md)

## Generate API Key

Follow the instructions [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/maximo/integration/api-keys.md)

## Object Accesses

Enable access to the following object structures.
- MXORGANIZATION
- MXITEM
- MXVENDORMSTR
- MXVENDOR
- MXGLCOMP
- MXCOA
- MXASSET
  
Follow the instructions [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/maximo/integration/api-keys.md)

Server restart is required.

## Enable Admin Mode

### Configure SMTP Server

Navigate to _System Properties_ under _Platform Configuration_

| Key            | Value              |
| -------------- | ------------------ |
| mail.smtp.host | smtp.gmail.com     |
| mail.smtp.port | 465                |
| mxe.adminEmai  | `<valid email id>` |

- Navigate to Database Configuration under Platform Configuration. Select "_Manage Admin Mode_".
- Set _Number of Administrative Sessions Allowed_ and _Number of Minutes for User Logout_ to 100.
- Update Properties.
- Click Turn Admin Mode On.
- Provide user _password_ and the _reason for change_.

### Disabe E-signature

If the following steps are not executed, the below error will be thrown when attempting to enable admin mode.
```
BMXAA3840E - The electronic signature entered is not valid for the user currently signed in to the application!
```

- Select Manage eSig Actions under Database Configuration.
- Under Applications select _Database Configuration_.
-Under _Options for Database Configuration_ disable _E-signature Enabled?_ for "_Apply Configuration Changes_" and "Manage Admin Mode", .
- Click OK and Save.

Server restart is required.

- Navigate to _Database Configuration_. Select _Manage Admin Mode_.
- Click _Turn Admin Mode On_.
