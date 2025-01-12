---
sidebar_position: 4
---

# Importing fal as a Python package

You may be interested in accessing dbt models and sources easily from a Python script.
For that, just use the `fal` package and intantiate a FalDbt project:

```py
from fal import FalDbt
faldbt = FalDbt(profiles_dir="~/.dbt", project_dir="../my_project")

faldbt.list_sources()
# [['results', 'ticket_data_sentiment_analysis']]

faldbt.list_models()
# {
#   'zendesk_ticket_metrics': <RunStatus.Success: 'success'>,
#   'stg_o3values': <RunStatus.Success: 'success'>,
#   'stg_zendesk_ticket_data': <RunStatus.Success: 'success'>,
#   'stg_counties': <RunStatus.Success: 'success'>
# }

sentiments = faldbt.source('results', 'ticket_data_sentiment_analysis')
# pandas.DataFrame
tickets = faldbt.ref('stg_zendesk_ticket_data')
# pandas.DataFrame
```

##  Interacting with dbt from a Notebook

It is also possible to import fal from a Notebook for rapid iteration on some ideas and to then make them scripts to [use as a pre-hook or post-hook of a dbt model](fal-cli/index.md).

We recommend it as an experimentation phase.

*****

Check out the [FalDbt class explanation](../Reference/faldbt-class-object.md) in the reference section.
