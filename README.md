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
  "content": [
    {
      "type": "text",
      "text": "# Product Review: "
    },
    {
      "type": "placeholder",
      "instructionType": "paragraph",
      "config": {
        "description": "Create a catchy product name for a wireless gaming headset",
        "tone": "enthusiastic",
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
        "description": "List 4 standout features of a premium gaming headset",
        "format": "bullet_points",
        "itemCount": 4
      }
    },
    {
      "type": "text",
      "text": "\n\n## Verdict\n\n"
    },
    {
      "type": "placeholder",
      "instructionType": "summary",
      "config": {
        "description": "Summarize why this headset is worth buying",
        "length": "brief"
      }
    }
  ]
}
```

**Compiles to AI Prompt:**

```
You are an AI designed to convert content templates into actual content.

# Product Review: <<Replace this placeholder with text using this user prompt: ([{<Create a catchy product name for a wireless gaming headset>}]). Format requirements: Use enthusiastic tone and short length (1-2 sentences).>>

## Key Features

<<Replace this placeholder with a list using this user prompt: ([{<List 4 standout features of a premium gaming headset>}]). Format requirements: Use bullet_points formatting with each item on a new line. Create exactly 4 items.>>

## Verdict

<<Replace this placeholder with a summary using this user prompt: ([{<Summarize why this headset is worth buying>}]). Format requirements: Use brief length (1-2 sentences).>>
```

## Getting Started

1. **[Read the specification](https://alexanderparker.github.io/instruction-template-specification/specification.html)** to understand the schema
2. **[Try the examples](https://alexanderparker.github.io/instruction-template-specification/examples.html)** to see templates in action
3. **[Build your own templates](https://alexanderparker.github.io/instruction-template-specification/getting-started.html)** using the schema

## Features

- 🎯 **Instruction-generative** - Placeholders become AI instructions, not data substitutions
- 📝 **Content-first authoring** - Write natural content with embedded placeholders
- 🔧 **Extensible type system** - Standard types plus custom instruction types
- ✅ **JSON Schema validation** - Full validation and tooling support
- 🌐 **Framework agnostic** - Works with any implementation
- 📚 **Rich instruction types** - Lists, paragraphs, tables, code blocks, and more

## Built-in Instruction Types

- **`list`** - Generate formatted lists with customizable styling
- **`paragraph`** - Create paragraphs with specified tone and length
- **`table`** - Generate tables with configurable format and dimensions
- **`code_block`** - Create code snippets with syntax highlighting
- **`dialogue`** - Generate conversations between multiple participants
- **`quote`** - Create relevant quotes with optional attribution
- **`summary`** - Generate summaries of varying detail levels
- **`image_description`** - Create descriptive text for images

## Use Cases

- **Content Marketing** - Email templates, blog post structures, social media content
- **Documentation** - Technical writing templates with dynamic sections
- **Education** - Lesson plan templates, assignment generators
- **Creative Writing** - Story structures, character development templates
- **Business** - Report templates, proposal frameworks

## Documentation

- **[Complete Specification](https://alexanderparker.github.io/instruction-template-specification/specification.html)** - Technical documentation with all instruction types
- **[Getting Started Guide](https://alexanderparker.github.io/instruction-template-specification/getting-started.html)** - Step-by-step tutorial for beginners
- **[Example Templates](https://alexanderparker.github.io/instruction-template-specification/examples.html)** - Template library with detailed breakdowns
- **[Schema Documentation](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/)** - Schema files and validation guide

## Community & Ecosystem

This specification is designed to enable a rich ecosystem of tools:

- **Visual Editors** - WYSIWYG template builders
- **Compilers** - Libraries that convert templates to prompts
- **Validators** - Tools that verify template correctness
- **Template Libraries** - Collections of reusable templates

## Contributing

We welcome contributions! You can help by:

- **Proposing schema improvements** via GitHub issues
- **Suggesting new instruction types** for the standard library
- **Improving documentation** with clearer examples
- **Sharing interesting use cases** and template examples

Open an issue or pull request on [GitHub](https://github.com/alexanderparker/instruction-template-specification) to get started.

## Versioning

ITS follows semantic versioning:

- **Major** versions introduce breaking changes to the schema
- **Minor** versions add new features while maintaining compatibility
- **Patch** versions fix issues without changing functionality

Current version: **v1.0**

## License

This specification is released under the [MIT License](LICENSE).
