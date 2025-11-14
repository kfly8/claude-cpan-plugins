---
name: generate-cpan-skill
description: Generate a Claude Skill from CPAN module documentation
params:
  - name: module_name
    type: string
    required: true
    description: Name of the CPAN module (e.g., Result::Simple)
  - name: synopsis
    type: string
    required: false
    description: Brief description of the module
---

# Generate CPAN Skill

This command generates a complete Claude Skill specification from CPAN module documentation. **It ALWAYS references the actual CPAN module documentation from MetaCPAN** to ensure accuracy.

## Process

1. **MetaCPAN Lookup**: First fetches the real module documentation from `https://metacpan.org/pod/[MODULE_NAME]`
2. **Analysis**: Analyzes the actual API, examples, and specifications
3. **Generation**: Creates the skill based on factual documentation

## Usage

```
/generate-cpan-skill --module_name "Result::Simple"
```

**Note**: The synopsis parameter is optional since the command will fetch the real description from MetaCPAN.

## Parameters

- **module_name** (required): The name of the CPAN module (will be verified on MetaCPAN)
- **synopsis** (optional): Override for the module description (otherwise fetched from MetaCPAN)

## Verification Process

The command will:
1. ✅ Verify the module exists on MetaCPAN
2. ✅ Fetch the real SYNOPSIS and DESCRIPTION
3. ✅ Extract actual API methods and their signatures
4. ✅ Copy verified usage examples
5. ✅ Include real dependencies and version info

## Example Output

Based on real MetaCPAN documentation, the command will generate:
1. **Concise skill** focused on essential usage
2. Core functions with practical examples
3. Key helper functions and patterns
4. Essential best practices
5. **Omits**: Installation, version history, extensive API docs

## Template

The generated skill follows this **concise** structure:

```markdown
---
name: [module-name]
description: [Brief purpose]
version: 1.0.0
tags: [perl, cpan, relevant-tags]
---

# [Module] - [Brief Purpose]

## Core Functions
[Essential functions with focused examples]

## Helper Functions
[Key helper functions if any]

## Practical Examples
[Real-world usage patterns]

## Best Practices
[Essential guidelines]
```