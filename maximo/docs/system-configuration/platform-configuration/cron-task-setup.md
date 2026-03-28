## Cron Task Setup

### Author: Jawahar

**Prerequiste**

Maximo installed and manage application accessible. Automation Script configured.

**Introduction**

Cron does stand for _command run on notice_. It is used to run periodically at a fixed time, date, or interval. 
As scheduled, it is known as a cron job. Although typically used to automate system maintenance and administration it can be used to automate any task.

**Create a Cron Task**

- Navigate to System Configuration -> Platform Configuration -> Cron Task Setup
- Click on _New Cron Task Definition_.

Provide the following information in the _Cron Task_ screen.

| Attribute                       | Value                                             |
|---------------------------------|---------------------------------------------------|
| Cron Task                       | CREATE-README                                     |
| Class                           | com.ibm.tivoli.maximo.script.ScriptCrontask       |
| Access Level                    | FULL                                              |

- Click + button in the _Cron Task Instances_. Provide the following information.
  
| Attribute                       | Value                                             |
|---------------------------------|---------------------------------------------------|
| Cron Task Instance Name         | CREATE-README                                     |
| Schedule                        | Every 1 minute(s)                                 |
| Run as User                     | MAXADMIN                                          |
| Active                          | Enable                                            |

- Under the Parameters segment

| Attribute                       | Value                                             |
|---------------------------------|---------------------------------------------------|
| SCRIPTARG                       |                                                   |
| SCRIPTNAME                      | CREATE-FILE                                       |

- Save the configuration.

**Success Criteria**

- Navigate to the /home/admin/apps/wlp/usr/servers/maximo directory.
- File readme.txt created with content Welcome to Maximo world !!

