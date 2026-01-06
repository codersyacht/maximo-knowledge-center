# Use-cases

Excessive Correlation Logging in system logs.

```CMD
[INFO] [MXServer] [CID-CRON-3592] Correlation started.
[INFO] [MXServer] [CID-CRON-3592] Correlation started, correlation data added:  TaskName:PlusABDIAsyncImmediateJobCron
[INFO] [MXServer] [CID-CRON-3592] Correlation started, correlation data added:  InstanceName:PlusABDIAsync_SyncFltData TaskName:PlusABDIAsyncImmediateJobCron
[INFO] [MXServer] [CID-CRON-3592] Correlation started, correlation data added:  InstanceName:PlusABDIAsync_SyncFltData TaskName:PlusABDIAsyncImmediateJobCron Activity:ACTION
[INFO] [MXServer] [CID-CRON-3591] Correlated data: BEGIN InstanceName:PlusABDIAsync_ChangePMStatus TaskName:PlusABDIAsyncImmediateJobCron Activity:ACTION ElapsedTime:69 ms  END
[INFO] [MXServer] [CID-CRON-3592] Correlated data: BEGIN InstanceName:PlusABDIAsync_SyncFltData TaskName:PlusABDIAsyncImmediateJobCron Activity:ACTION ElapsedTime:56 ms  END
```

**Solution**

Option 1:

Disable th following System Properties _mxe.logging.CorrelationEnabled_ Reference [here](https://www.ibm.com/docs/en/masv-and-l/maximo-manage/cd?topic=filter-correlation-related-events-in-logs)

- Navigate to Platform Configuration -> System Properties.
- Search for _mxe.logging.CorrelationEnabled_.
- Change the value to 0.

Option 2:

The setting can also be made through maximo.properties file.

- Update maximo.properties with the following entry:
- mxe.logging.CorrelationEnabled=0.
- Rebuild the ear and deploy.

