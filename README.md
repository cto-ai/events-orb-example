# events-orb-example
An example showing how to use the CTO.ai CircleCI Orb to use the Events API. This enables Workflow Metrics.

User must set a secret environment variable for their Events API Token in the CircleCI settings. This could be in a CircleCI Context, in their Organization Settings, or their Project Settings. The secret must then be accessed from the user's CircleCI config (e.g. `${CTOAI_EVENTS_API_TOKEN}` and passed to the Orb in order to access the Events API.

The `team_id` must also be passed to the Orb, and the user could put this in an environment variable too, though it is not strictly necessary, as `team_id` is not a secret. The user could put their `team_id` directly in their config if they wish.

More information is available at the CTO.ai documentation for the Events API: https://cto.ai/docs/workflow-metrics-api
