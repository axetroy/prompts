---
title: Generate Prompt Template
description: Generate a reusable prompt template from the user's input while preserving its intent, context, constraints, tone, and expected output format.
tags:
  - generation
  - prompt
  - template
---

Here is the user's input in **UserInput** block that needs to be transformed into a reusable prompt template:

<UserInput name="user_input" description="The user's original instruction, task description, requirements, or desired behavior">
  {user_input}
</UserInput>

Generate a reusable prompt template based on the user's input.

The goal is to transform the user's specific instruction into a **general-purpose, reusable prompt template** without changing its original intent.

### Template Generation Rules

The generated prompt template should:

- Clearly identify the task, objective, and expected behavior.
- Preserve the original intent, context, constraints, requirements, tone, and output expectations.
- Generalize values that are likely to change between uses into `<VAR>` blocks.
- Keep instructions, rules, logic, and other reusable content outside of `<VAR>` blocks.
- Only introduce variables when a value is genuinely expected to change between uses. Do not turn every noun or phrase into a variable.
- Give every variable a concise, descriptive `name`.
- Give every variable a clear `description` explaining what the variable represents and how it should be used.
- Add a `defaultValue` when a sensible default can be inferred from the user's input. Do not invent a default value when none is implied.
- Preserve important examples, terminology, formatting conventions, and constraints from the original input when they contribute to the behavior of the template.
- Make the generated template self-contained so it can be used without access to the original user input.
- Do not introduce new requirements, assumptions, constraints, or behavior that are not supported by the user's input.
- Prefer explicit instructions over vague descriptions.
- Use Markdown formatting when it improves readability.
- Add a **Response Format** section when the expected response structure or output constraints can be inferred.
- If the original input specifies a strict output format, preserve that format as closely as possible.
- If the original input does not specify an output format, do not invent an unnecessarily restrictive one.

### Metadata Rules

The generated template must begin with YAML front matter containing:

- `title`: A concise, descriptive title that summarizes what the prompt template does. Use title case.
- `description`: A short description of the template's purpose and transformation behavior. It should be specific enough to distinguish the template from similar templates.
- `tags`: A short list of relevant lowercase tags describing the template's primary function and domain.

Metadata should describe the **generated template itself**, not the user's original input.

Avoid adding unnecessary metadata fields unless they are clearly useful.

### Variable Rules

Use the following format for dynamic values:

<VAR name="variable_name" description="Description of the variable" defaultValue="Optional default value">{variable_name}</VAR>

Variable names should:

- Be concise and descriptive.
- Use `snake_case`.
- Describe the value rather than its purpose when possible.
- Remain consistent throughout the template.
- Never contain spaces or special characters.

Use `defaultValue` only when a meaningful default is explicitly provided or can be safely inferred from the original input.

For example:

<VAR name="language" description="The programming language to use" defaultValue="JavaScript">{language}</VAR>

If no meaningful default exists, omit the `defaultValue` attribute:

<VAR name="topic" description="The topic to write about">{topic}</VAR>

### Example

For example, if the user's input is:

<UserInput name="user_input" description="The user's original instruction">
  Write a concise product description for a new smartphone. Highlight its camera, battery life, and performance. Keep the tone professional and limit the response to 100 words.
</UserInput>

A suitable generated prompt template would be:

```md
---
title: Generate Product Description
description: Generate a concise professional product description that highlights key product features while respecting a specified word limit.
tags:
  - writing
  - product
  - description
---

Write a concise product description for the following product:

<Product>
<VAR name="product" description="The product to describe">{product}</VAR>
</Product>

Highlight the following key features:

<Features>
<VAR name="features" description="The product features that should be emphasized" defaultValue="camera, battery life, and performance">{features}</VAR>
</Features>

Use a professional tone and keep the response within:

<WordLimit>
<VAR name="word_limit" description="The maximum number of words allowed in the response" defaultValue="100">{word_limit}</VAR>
</WordLimit>

### Response Format

Return only the product description.
```

### Response Requirements

Return only the generated prompt template. Do not include explanations, analysis, comments, or code fences.

The generated template must follow the structure and conventions described above.
