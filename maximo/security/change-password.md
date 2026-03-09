# Change Password

- Login to Manage application using super user.
  ```URL
  https://admin.codehub1.fyre.ibm.com/
  ```
- On the left hand sidebar, navigate to Suite -> Security -> Users.
- Search for MAXADMIN user and select the user.
- Click onto the edit icon.
- By default the Authentication type under the Authentication section will be set to Local. Expand the authentication.
- Click "Replace forgotten password".
- Choose Custom password.
- Provide a new password. example: LabMachine4@Training.
- Save. 
- Logout.
- Login back to manage application with username/password as maxadmin/LabMachine4@Training.

### Note:

This changes the token value in the the Users collection in the mongodb mas_max_core db.

```CMD
admin> show databases
admin                  100.00 KiB
config                 108.00 KiB
ibm-sls_sls_licensing    1.39 MiB
local                   76.00 KiB
mas_max_adoptionusage  644.00 KiB
mas_max_catalog        136.00 KiB
mas_max_core           948.00 KiB
admin> use mas_max_core
switched to db mas_max_core
mas_max_core> db.User.find({username: 'maxadmin'}) 
```
```
token: '1000:e8ebdcd2427a5409009bd64748cad0fa3f60ae70a16c13dd:cd3e3b06af13ecf1a827cbc1c782d88866d149ec9f543b6d'
```

## Login to Manage application

```URL
max-all.manage.codehub1.fyre.ibm.com/maximo
```
