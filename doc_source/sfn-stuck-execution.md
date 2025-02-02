# Use timeouts to avoid stuck executions<a name="sfn-stuck-execution"></a>

By default, the Amazon States Language doesn't set timeouts in state machine definitions\. Without an explicit timeout, Step Functions often relies solely on a response from an activity worker to know that a task is complete\. If something goes wrong and `TimeoutSeconds` isn't specified, an execution is stuck waiting for a response that will never come\.

To avoid this, specify a reasonable timeout when you create a task in your state machine\. For example: 

```
"ActivityState": {
  "Type": "Task",
  "Resource": "arn:aws:states:us-east-1:123456789012:activity:HelloWorld",
  "TimeoutSeconds": 300,
  "HeartbeatSeconds": 60,
  "Next": "NextState"
}
```

For more information, see [Task](amazon-states-language-task-state.md) in the Amazon States Language documentation\.

**Note**  
You can set a timeout for your state machine using the `TimeoutSeconds` field in your Amazon States Language definition\. For more information, see [State Machine Structure](amazon-states-language-state-machine-structure.md)\.