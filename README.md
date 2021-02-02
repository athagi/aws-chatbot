# aws-chatbot
## outline
This template create Aws chatbot related stacks.

## usage
Need to init aws chatbot and slack workspace relation in AWS console at first.

### budget.yaml
This template creates AWS bugets and chatbot notification by slack.  
When your cost exceeded *AlertThresholdPercentage* of *MonthlyCostBudget*, the notification goes to *SlackChannelId* channel in your *SlackWorkspaceId* slack workspace.

```
aws cloudformation deploy \
  --template-file budget.yaml \
  --stack ${stack_name} \
  --capabilities CAPABILITY_IAM \
  --parameter-overrides MonthlyCostBudget=8 AlertThresholdPercentage=90 SlackChannelId=${slack_channel_id} SlackWorkspaceId=${slack_workspace_id}
```

### slack-aws-cli.yaml
This template creates AWS chatbot for slack @aws commands.
Currently, this command allow to execute `aws ecr` command.

```
aws cloudformation deploy --template-file slack-aws-cli.yaml --stack slack-aws-cli --capabilities CAPABILITY_IAM --parameter-overrides SlackChannelId=${slack_channel_id} SlackWorkspaceId=${slack_workspace_id}
```