---
title: Transform Environment Variables
description: Transform environment variables from one format to another while preserving meaning, tone, and formatting.
tags:
  - transformation
  - environment
---

Here is the environment variable in **SourceText** block that needs to be transformed:

<SourceText>
<VAR name="env_variable_to_be_transformed" description="The environment variable that needs to be transformed">
  {env_variable_to_be_transformed}
</VAR>
</SourceText>

Try to transform the environment variable to **<VAR name="target" description="The target format for transformation" defaultValue="PowerShell">{target}</VAR>**

### Response Format

Return **only** the transformed environment variable.
