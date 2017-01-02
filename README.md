# Ensemble-Interface-DiskSpace-Test
A framework to test for disk space consumption for Ensemble interfaces. 

It has a dual purpose - 
To aid in estimating the required disk space interfaces will consume (both database file growth and journal files) 
As well as verifying the Ensemble Purge mechanism will indeed clean out all the interfaces' related data 

See class reference (specifically of the InterfaceDiskSpace.Main class) for documentation and usage guidelines

Here is a sample Output -
You can see for example it points out an issue with certain persistent entities referenced by Web Service responses that are not deleted by default by the Purge process.

ENSEMBLE>write ##class(InterfaceDiskSpace.Main).PreTestRun(.runId)
 
Stopping Production...
 
17:17:30.986:Ens.Director: StopProduction initiated.
17:17:30.986:Ens.Job: System is quiescent
17:17:30.986:Ens.Job: Requesting all jobs to terminate ...
17:17:31.005:Ens.Director: Production 'Test.WSTimeouts.Production' stopped.
Cleaning Production...
Confirm cleaning data <y/n>?
y
Purging...
 
Purged:
deleteCounts=""
deleteCounts("Bitmap Chunks")=0
deleteCounts("Business Processes")=0
deleteCounts("Business Rule Logs")=0
deleteCounts("Ensemble Messages")=0
deleteCounts("Event Logs")=11
deleteCounts("Host Monitor Data")=31
deleteCounts("I/O Logs")=0
deleteCounts("Managed Alerts")=0
deleteCounts("Message Bodies")=0
 
Switching Journal...
Capturing data...
1
ENSEMBLE>write ##class(InterfaceDiskSpace.Main).TestSummary(runId)
1
ENSEMBLE>write ##class(InterfaceDiskSpace.Main).PurgeTest(runId,1)
 
 
Purged:
deleteCounts=""
deleteCounts("Bitmap Chunks")=0
deleteCounts("Business Processes")=0
deleteCounts("Business Rule Logs")=0
deleteCounts("Ensemble Messages")=102
deleteCounts("Event Logs")=33
deleteCounts("Host Monitor Data")=9
deleteCounts("I/O Logs")=0
deleteCounts("Managed Alerts")=0
deleteCounts("Message Bodies")=101
 
1
ENSEMBLE>write ##class(InterfaceDiskSpace.Main).Report(runId)
 
 
Data Usage Report
===========================
 
Database file size used: 1
Journal file size used: 0
Journal space used: 325108
 
Globals growth
----------------------
Ens.MessageBodyD                                                                     .007
Ens.MessageHeaderD                                                                   .02
Ens.MessageHeaderI                                                                   .003
Ens.Util.LogD                                                                        .004
ITest.Proxy.s0.AddressD            ITest.Proxy.s0.Address.cls                        .004
ITest.Proxy.s0.PersonD             ITest.Proxy.s0.Person.cls                         .003
 
Journal Profile
----------------------
Ens.ActiveMessage                                                                    26184
Ens.BusinessProcessD                                                                 3308
Ens.BusinessProcessI                                                                 1456
Ens.Configuration                                                                    424
Ens.JobRequest                                                                       132
Ens.JobStatus                                                                        112
Ens.MessageBodyD                                                                     19508
Ens.MessageHeaderD                                                                   34624
Ens.MessageHeaderI                                                                   89540
Ens.Queue                                                                            37996
Ens.Runtime                                                                          50920
Ens.Suspended                                                                        100
Ens.Util.LogD                                                                        10404
Ens.Util.LogI                                                                        12248
ITest.Proxy.s0.AddressD            ITest.Proxy.s0.Address.cls                        16096
ITest.Proxy.s0.PersonD             ITest.Proxy.s0.Person.cls                         8624
 
Globals remaining after purge
----------------------
ITest.Proxy.s0.AddressD            ITest.Proxy.s0.Address.cls                        .004
ITest.Proxy.s0.PersonD             ITest.Proxy.s0.Person.cls                         .003
1
