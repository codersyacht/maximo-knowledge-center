# Debug Data Capture

### Author: Mohamed Jawahar Hussain

### Prerequisite: Liberty server up and running.

## Execution Steps

Navigate to bin directory of wlp.

```CMD
cd /home/admin/apps/wlp/bin
```

**Thread dumps:**

./server javadump defaultServer --include=thread

**Heap Dumps**

./server javadump defaultServer --include=heap

**Core dumps**

./server dump defaultServer --include=system

## Success Metric

Message displays the path and the file generated.


