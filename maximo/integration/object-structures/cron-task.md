## Cron Task

### Author: Jawahar

### Create Cron Task

Code sample for Cron Task:
```Java
package cron;



import java.util.Date;
import psdi.app.system.CrontaskParamInfo;
import psdi.server.SimpleCronTask;

public class CronJob extends SimpleCronTask
{

	private static CrontaskParamInfo[] params = null; 
	static
	 {
		 params = new CrontaskParamInfo[2];
		 params[0] = new CrontaskParamInfo();
		 params[0].setName("QUEUETABLE");
		 params[1] = new CrontaskParamInfo();
		 params[1].setName("EXTSYSNAME");
	 }
	 
	 @Override
	public CrontaskParamInfo[] getParameters() 
	 {
	     return params;
	 }
	 
	@Override
	public void cronAction() throws Exception 
	 {
		try 
		{
          
			  System.out.println("Sample Cron Task Execution Begin");
			  System.out.println("Current Date and Time: " + new Date());
			  System.out.println("Parameters: ");
			  System.out.println(getParamAsString("QUEUETABLE"));
			  System.out.println(getParamAsString("EXTSYSNAME"));			  
			  System.out.println("Sample Cron Task Execution End");
			  
        }
        catch (Exception e) 
		{
            e.printStackTrace();
        }
		
	}
	
	public static void main (String args[])
	
	{
		try
		{
		CronJob cj = new CronJob();
		cj.cronAction();
		}
		catch (Exception e)
		{
			e.printStackTrace();
		}
	}
}
```
