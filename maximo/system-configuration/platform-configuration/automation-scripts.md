## Automation Scripts

### Author: Jawahar

**Prerequiste**

Maximo installed and manage application accessible.

**Introduction**

Automation Scripts are used to execute a custom logic at a configured interval period. Automation scripts are normally used in conjuction with cron task.

**Create Automation Scripts**

- Navigate to System Configuration -> Platform Configuration -> Automation Scripts
- Under "More Actions" select Create and click Script.

Provide the following information in the _Create Script_ screen.

| Attribute                       | Value        |
|---------------------------------|--------------|
| Script                          | CREATE-FILE  |
| Script Language                 | python       |
| Active                          | Enable       |

- Click Create
- Once the the script is created, the script will be visible with the name in the Scripts list view.
- Select the newly created script.
- In the _text-area_ below the attribute settings, add the below content:

```python

file_object = open("/home/admin/apps/wlp/usr/servers/maximo/readme.txt", "w")
# Write some content to the file
file_object.write("Welcome to Maximo world !! ")
# Close the file to save the changes
file_object.close()

```

- Save the configuration.

**Success Criteria**

On saving the configuration the following message should be displayed _BMXAA4205I - Record has been saved_.

**Next Step**

Create cron task.
