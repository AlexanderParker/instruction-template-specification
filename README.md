# Instruction Template Specification (ITS)

[![Schema Version](https://img.shields.io/badge/schema-v1.0-blue)](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)

A specification for **instruction-generative content templates** that compile into AI prompts. Unlike traditional templating systems that substitute data into templates, ITS converts content templates with placeholders into structured instructions for AI content generation.

## What is ITS?

ITS enables content creators to build templates using natural language and visual placeholders, which then compile into prompts that instruct AI systems to generate specific types of content.

### Traditional Templating vs ITS

```
Traditional: Template + Data → Content
ITS:         Template → AI Prompt → AI-Generated Content
```

## Quick Example

**Template:**

```json
{
  "$schema": "https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-base-schema-v1.json",
  "version": "1.0.0",
  "metadata": {
    "name": "Product Review Template",
    "description": "Template for generating product reviews"
  },
  "variables": {
    "productType": "wireless gaming headset",
    "includeSpecs": true
  },
  "content": [
    {
      "type": "text",
      "text": "# Product Review: "
    },
    {
      "type": "placeholder",
      "instructionType": "title",
      "config": {
        "description": "Create a catchy product name for a ${productType}",
        "style": "catchy",
        "length": "short"
      }
    },
    {
      "type": "text",
      "text": "\n\n## Key Features\n\n"
    },
    {
      "type": "placeholder",
      "instructionType": "list",
      "config": {
        "description": "List 4 standout features of a premium ${productType}",
        "format": "bullet_points",
        "itemCount": 4
      }
    },
    {
      "type": "conditional",
      "condition": "includeSpecs == true",
      "content": [
        {
          "type": "text",
          "text": "\n\n## Technical Specifications\n\n"
        },
        {
          "type": "placeholder",
          "instructionType": "table",
          "config": {
            "description": "Create a specs table for a ${productType} with frequency response, impedance, and connectivity",
            "format": "markdown",
            "columns": 2,
            "rows": 3
          }
        }
      ]
    },
    {
      "type": "text",
      "text": "\n\n## Verdict\n\n"
    },
    {
      "type": "placeholder",
      "instructionType": "summary",
      "config": {
        "description": "Summarize why this ${productType} is worth buying",
        "length": "brief"
      }
    }
  ]
}
```

**Compiles to AI Prompt:**

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

# Product Review: <<Replace this placeholder with a title using this user prompt: ([{<Create a catchy product name for a wireless gaming headset>}]). Format requirements: Create a catchy title that is short in length.>>

## Key Features

<<Replace this placeholder with a list using this user prompt: ([{<List 4 standout features of a premium wireless gaming headset>}]). Format requirements: Use bullet_points formatting with each item on a new line.>>

## Technical Specifications

<<Replace this placeholder with a table using this user prompt: ([{<Create a specs table for a wireless gaming headset with frequency response, impedance, and connectivity>}]). Format requirements: Use markdown format.>>

## Verdict

<<Replace this placeholder with a summary using this user prompt: ([{<Summarize why this wireless gaming headset is worth buying>}]). Format requirements: Use brief length (1-2 sentences).>>
```

## Key Features

### 🎯 **Variables & Conditionals**

- Define reusable variables with `${variableName}` syntax
- Use conditionals to include/exclude sections dynamically
- Support for strings, numbers, booleans, objects, and arrays
- JavaScript-like expressions in conditions

### 📚 **Rich Instruction Types**

Built-in types include:

- `title` - Headlines with style control
- `list` - Formatted lists (bullets, numbers, etc.)
- `paragraph` - Text with tone and length control
- `table` - Structured data tables
- `code_block` - Code snippets with syntax highlighting
- `dialogue` - Multi-person conversations
- `quote` - Quotes with attribution
- `summary` - Summaries of varying detail
- `image_description` - Descriptive image text

### 🔧 **Extensible Type System**

- Create custom instruction types for your domain
- Share types across templates with schema extension
- Override standard types with your own implementations

### ✅ **Schema Validation**

- Full JSON Schema validation
- Type extension validation
- Rich tooling support in modern editors

## Getting Started

1. **[Read the specification](https://alexanderparker.github.io/instruction-template-specification/specification.html)** to understand the schema
2. **[Try the examples](https://alexanderparker.github.io/instruction-template-specification/examples.html)** to see templates in action
3. **[Build your own templates](https://alexanderparker.github.io/instruction-template-specification/getting-started.html)** using the schema

## Documentation

- **[Complete Specification](https://alexanderparker.github.io/instruction-template-specification/specification.html)** - Technical documentation with all features
- **[Getting Started Guide](https://alexanderparker.github.io/instruction-template-specification/getting-started.html)** - Step-by-step tutorial
- **[Example Templates](https://alexanderparker.github.io/instruction-template-specification/examples.html)** - Real-world examples
- **[Schema Extension Example](https://alexanderparker.github.io/instruction-template-specification/examples/schema-extension/)** - How to extend and override types
- **[Schema Files](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/)** - JSON Schema definitions

## Schema Files

### Core Schemas

- **[Base Schema](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-base-schema-v1.json)** - Defines template structure
- **[Type Extension Schema](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-type-extension-schema-v1.json)** - Validates type extension files
- **[Standard Types](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-standard-types-v1.json)** - Built-in instruction types

## Use Cases

- **Content Marketing** - Email templates, blog structures, social media posts
- **Documentation** - API docs, user guides, FAQs with dynamic content
- **Education** - Lesson plans, assignment generators, course outlines
- **Creative Writing** - Story structures, character profiles, dialogue scenes
- **Business** - Reports, proposals, presentations with AI-generated sections

## Community & Ecosystem

This specification is designed to enable:

- **Visual Editors** - WYSIWYG template builders
- **Compilers** - Tools that convert templates to prompts
- **Type Libraries** - Reusable instruction type collections
- **Template Marketplaces** - Share and discover templates

## Contributing

We welcome contributions! You can help by:

- **Proposing improvements** via GitHub issues
- **Creating new instruction types** for specific domains
- **Building tools** that implement the specification
- **Sharing templates** and use cases

See our [GitHub repository](https://github.com/alexanderparker/instruction-template-specification) to get started.

## Versioning

ITS follows semantic versioning:

- **Major** versions introduce breaking changes
- **Minor** versions add new features backward-compatibly
- **Patch** versions fix issues without changing functionality

Current version: **v1.0**

## License

This specification is released under the [MIT License](LICENSE).

---

Built with ❤️ for the AI content generation community
