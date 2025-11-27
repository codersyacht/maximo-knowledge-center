## Cron Task

### Author: Jawahar

### Create Cron Task

Download the sample code [here](https://github.com/codersyacht/maximo-knowledge-center/blob/main/maximo/integration/CronJob.java).

Package the code to a jar file and make sure to include the package in the application classpath.

### Configure Crok Task

In Manage application,

-Navigate to System Configuration -> Platform Configuration -> Cron Task Setup.
-Click New Cron Task Definition.

| Attribute     | Value         |
| :------------ | :-----------: |
| Cron Task     | CronJob       |
| Description   | CronJob       |
| Class         | cron.CronJob  |

### Cron Task Instance

Create a new Cron Task Instance with the following properties:

| Attribute                     | Value             |
| :---------------------------- | :---------------: |
| Cron Task Instance Name       | CronJob           |
| Description                   | CronJob           |
| Schedule                      | Every 30 seconds  |
| Run as User                   | MAXADMIN          |
| Active                        | Enable            |

### Parameters

| Attribute                     | Value             |
| :---------------------------- | :---------------: |
| EXTSYSNAME                    | External System   |
| QUEUETABLE                    | Local Queue       |

Save the settings.
