
## DB2 Backup and Restore
  
  **Setting DB2INSTANCE:**

  ```CMD
  export DB2INSTANCE=db2inst1
  ```

  **Backup Database**

```CMD
mkdir -p dbbackup/manage/V1
```

  ```CMD
  db2 backup db MAXIMO to /home/db2inst1/dbbackup/manage/V1
  ```

  **Restore Database**

  ```CMD
  db2 restore db MAXIMO from /home/db2inst1/dbbackup/V1
  ```
