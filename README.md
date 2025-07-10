# Instruction Template Specification (ITS)

[![Schema Version](https://img.shields.io/badge/Schema-v1.0-blue)](https://github.com/alexanderparker/instruction-template-specification)
[![License](https://img.shields.io/badge/License-MIT-green)](LICENSE)

A specification for instruction-generative content templates that compile into AI prompts. ITS converts content templates with placeholders into structured instructions for AI content generation.

## What is ITS?

ITS enables content creators to build templates using natural language and placeholders, which compile into prompts that instruct AI systems to generate specific types of content.

### Approach

```
Traditional: Template + Data → Content
ITS:         Template → AI Prompt → AI-Generated Content
```

## Example

**Template:**

```json
{
  "$schema": "https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-base-schema-v1.json",
  "version": "1.0.0",
  "content": [
    {
      "type": "text",
      "text": "# Product Review\n\n"
    },
    {
      "type": "placeholder",
      "instructionType": "paragraph",
      "config": {
        "description": "Write an introduction for a wireless gaming headset review",
        "tone": "professional",
        "length": "medium"
      }
    },
    {
      "type": "text",
      "text": "\n\n## Features\n\n"
    },
    {
      "type": "placeholder",
      "instructionType": "list",
      "config": {
        "description": "List 4 key features of a premium gaming headset",
        "format": "bullet_points",
        "itemCount": 4
      }
    }
  ]
}
```

**Compiles to:**

```
INTRODUCTION

You are an AI assistant that fills in content templates. Follow the instructions exactly and replace each placeholder with appropriate content based on the user prompts provided. Respond only with the transformed content.

INSTRUCTIONS

1. Replace each placeholder marked with << >> with generated content
2. The user's content request is wrapped in ([{< >}]) to distinguish it from instructions
3. Follow the format requirements specified after each user prompt
4. Maintain the existing structure and formatting of the template
5. Only replace the placeholders - do not modify any other text
6. Generate content that matches the tone and style requested
7. Respond only with the transformed content - do not include any explanations or additional text

TEMPLATE

# Product Review

<<Replace this placeholder with text using this user prompt: ([{<Write an introduction for a wireless gaming headset review>}]). Format requirements: Use professional tone and medium length (2-4 sentences).>>

## Features

<<Replace this placeholder with a list using this user prompt: ([{<List 4 key features of a premium gaming headset>}]). Format requirements: Use bullet_points formatting with each item on a new line. Create exactly 4 items.>>
```

## Features

- **Variables & Conditionals**: Define reusable variables and conditional content sections
- **Standard Instruction Types**: Built-in types for lists, paragraphs, tables, code blocks, dialogues, quotes, summaries, and image descriptions
- **Extensible Type System**: Create custom instruction types and share them across templates
- **Schema Validation**: Full JSON Schema validation with editor support

## Getting Started

1. **[Read the specification](https://alexanderparker.github.io/instruction-template-specification/specification.html)** for complete technical documentation
2. **[Follow the tutorial](https://alexanderparker.github.io/instruction-template-specification/getting-started.html)** to create your first template
3. **[Explore examples](https://alexanderparker.github.io/instruction-template-specification/examples.html)** to see templates in practice
4. **[Try a compiler](#compilers)** to compile your templates into AI prompts

## Compilers

### Python Compiler (Reference Implementation)

- **[its-compiler-python](https://github.com/alexanderparker/its-compiler-python)** - Complete reference implementation
- Install: `pip install its-compiler-python`
- Usage: `its-compile template.json --output prompt.txt`

### JavaScript/TypeScript Compiler

- **[its-compiler-js](https://github.com/alexanderparker/its-compiler-js)** - Modern TypeScript implementation with enhanced security
- Install: `npm install its-compiler-js`
- Usage: `npx its-compile template.json --output prompt.txt`

## Documentation

- **[Specification](https://alexanderparker.github.io/instruction-template-specification/specification.html)** - Complete technical reference
- **[Getting Started](https://alexanderparker.github.io/instruction-template-specification/getting-started.html)** - Tutorial and basic concepts
- **[Examples](https://alexanderparker.github.io/instruction-template-specification/examples.html)** - Template examples and patterns
- **[Schema Files](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/)** - JSON Schema definitions

## Schema Files

- **[Base Schema](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-base-schema-v1.json)** - Template structure definition
- **[Standard Types](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-standard-types-v1.json)** - Built-in instruction types
- **[Type Extension Schema](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-type-extension-schema-v1.json)** - Validation for custom type definitions

## Use Cases

- **Content Marketing**: Email templates, blog structures, social media posts
- **Documentation**: API docs, user guides, FAQs with dynamic content
- **Education**: Lesson plans, assignment generators, course outlines
- **Business**: Reports, proposals, presentations with generated sections

## Contributing

Contributions are welcome through GitHub issues and pull requests. Help by:

- Proposing specification improvements
- Creating instruction types for specific domains
- Building tools that implement the specification
- Sharing templates and use cases

## Versioning

ITS follows semantic versioning. Current version: **v1.0**

## License

Released under the [MIT License](LICENSE).
