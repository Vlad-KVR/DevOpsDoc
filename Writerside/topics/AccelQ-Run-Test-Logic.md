# AccelQ Run Test Logic

When you launch an AccelQ Test (it doesn't matter from a branch or via a pipeline) the runTest method is called in the apex, which schedules AccelqExecuteScheduler and creates AccelQ Test Result, Metadata Log.

When the scheduler starts for the first time, we will make a request to the Trigger Job endpoint (see APIs section). After that, we will launch the same scheduler in 1 minute.

When the scheduler starts the second time we will try to get the test results(Get Job Result in APIs section). If the tests are in progress, we will restart the scheduler every minute until we get the test results (or an error).

After we have received the result, we will create an AccelQ One Test Result for each AccelQ test and also update the AccelQ Test Result, Metadata Log.

If this was done via pipeline, then after updating the Metadata Log, a trigger will be triggered that will launch the next step if necessary.
