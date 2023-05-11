# CircleCI Orb for CTO.ai Workflow Metrics

If your CICD runs on CircleCI, you can use the CTO.ai CircleCI Orb to make it easier to instrument your CICD with [workflow events](https://cto.ai/docs/workflow-metrics). The Orb can be accessed with this stanza in your CircleCI configuration yaml:

```
orbs:
  cto-ai: cto-ai/cto-ai@1.0.1
```

Use the Orb to send events to CTO.ai by calling it from your `steps`:

```
      steps:
        - cto-ai/event:
            token: ${CTOAI_EVENTS_API_TOKEN}
            team_id: ${CTOAI_EVENTS_API_TEAM_ID}
            event_name: deployment
            event_action: succeeded
            branch: ticket-id-123
            commit: pipeline-label-A1
            image: branch-label-543
            name: user
```

Note: only `token` and `team_id` are required fields. The other fields are optional.

`CTOAI_EVENTS_API_TOKEN` is a secret environment variable provided by CTO.ai that you set in your CircleCI config, and then pass to the Orb. If you don't have a token, instructions on how to get one are available here: https://cto.ai/docs/workflow-metrics-api. 

You can set your environmenta variables in a CircleCI Context, in your Organization Settings, or on your Project Settings. The environment variable must then be accessed from the user's CircleCI config (e.g. `CTOAI_EVENTS_API_TOKEN` as seen above) and passed to the Orb to use the CTO.ai Events API.

The `team_id` is also a required field, and could also be accessed using an environment variable as shown in the example above. Since the `team_id` is not a secret, however, this is not strictly necessary. It could be supplied directly in your config file. 

More information on CTO.ai Workflow Metrics: https://cto.ai/docs/workflow-metrics

More information on the CTO.ai Events API: https://cto.ai/docs/workflow-metrics-api
