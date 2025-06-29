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
  "content": [
    {
      "type": "text",
      "text": "Here are some popular citrus fruits:\n"
    },
    {
      "type": "placeholder",
      "instructionType": "list",
      "config": {
        "description": "list 5 different citrus fruits",
        "format": "bullet_points"
      }
    }
  ]
}
```

**Compiles to:**

```
You are an AI designed to convert content templates into actual content.

Here are some popular citrus fruits:

<<Replace this section with a list. list 5 different citrus fruits. Each list item goes on its own line. Use bullet_points to separate each item.>>
```

## Schema Documentation

- **[Base Schema](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-base-schema-v1.json)** - Core template structure
- **[Standard Types](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-standard-types-v1.json)** - Built-in instruction types
- **[Full Documentation](https://alexanderparker.github.io/instruction-template-specification/)** - Complete specification guide

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

## Getting Started

1. **[Read the specification](https://alexanderparker.github.io/instruction-template-specification/)** to understand the schema
2. **[Try the examples](https://alexanderparker.github.io/instruction-template-specification/examples/)** to see templates in action
3. **[Build your own templates](https://alexanderparker.github.io/instruction-template-specification/getting-started/)** using the schema

## Use Cases

- **Content Marketing** - Email templates, blog post structures, social media content
- **Documentation** - Technical writing templates with dynamic sections
- **Education** - Lesson plan templates, assignment generators
- **Creative Writing** - Story structures, character development templates
- **Business** - Report templates, proposal frameworks

## Schema Documentation

- **[Schema v1.0 Overview](https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/)** - Schema files and validation guide
- **[Complete Specification](https://alexanderparker.github.io/instruction-template-specification/specification.html)** - Technical documentation with all instruction types
- **[Example Templates](https://alexanderparker.github.io/instruction-template-specification/examples.html)** - Template library with detailed breakdowns

### Quick Template Structure

**Template Example:**

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

# Product Review: <<Replace this paragraph with: Create a catchy product name for a wireless gaming headset. Tone: enthusiastic. Length: short (1-2 sentences).>>

## Key Features

<<Replace this section with a list. List 4 standout features of a premium gaming headset. Each list item goes on its own line. Use bullet_points to separate each item. Create exactly 4 items.>>

## Verdict

<<Replace this section with a summary. Summarize why this headset is worth buying. Length: brief (1-2 sentences).>>
```

## Community & Ecosystem

This specification is designed to enable a rich ecosystem of tools:

- **Visual Editors** - WYSIWYG template builders
- **Compilers** - Libraries that convert templates to prompts
- **Validators** - Tools that verify template correctness
- **Template Libraries** - Collections of reusable templates

## Contributing

We welcome contributions to the specification:

1. **Schema improvements** - Propose enhancements to the core schema
2. **New instruction types** - Suggest additions to the standard types library
3. **Documentation** - Help improve clarity and examples
4. **Use cases** - Share interesting applications of the specification

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Versioning

ITS follows semantic versioning:

- **Major** versions introduce breaking changes to the schema
- **Minor** versions add new features while maintaining compatibility
- **Patch** versions fix issues without changing functionality

Current version: **v1.0**

## License

This specification is released under the [MIT License](LICENSE).

---

**Schema URLs:**

- Base Schema: `https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-base-schema-v1.json`
- Standard Types: `https://alexanderparker.github.io/instruction-template-specification/schema/v1.0/its-standard-types-v1.json`
- Documentation: `https://alexanderparker.github.io/instruction-template-specification/`
