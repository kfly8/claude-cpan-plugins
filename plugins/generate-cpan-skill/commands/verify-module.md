---
name: verify-cpan-module
description: Verify that a CPAN module exists and fetch its basic information
params:
  - name: module_name
    type: string
    required: true
    description: Name of the CPAN module to verify
---

# Verify CPAN Module

This command verifies that a CPAN module exists on MetaCPAN and fetches its basic information before generating skills.

## Usage

```
/verify-cpan-module --module_name "Result::Simple"
```

## Process

1. **Existence Check**: Verifies the module exists on MetaCPAN
2. **Information Fetch**: Retrieves basic module information
3. **API Preview**: Shows available methods/functions (if detectable)
4. **Readiness Assessment**: Confirms if the module is ready for skill generation

## Output

The command will display:
- ✅ Module existence status
- 📝 Module description and version
- 👤 Author information  
- 🏷️ Tags and keywords
- 📚 Available documentation sections
- ⚠️ Any potential issues for skill generation

## Example Output

```
✅ Module Found: Result::Simple v0.05
📝 Description: A dead simple perl-ish Result like F#, Rust, Go, etc.
👤 Author: KFLY
🏷️ Keywords: result, error-handling, functional
📚 Sections: SYNOPSIS, DESCRIPTION, FUNCTIONS, EXAMPLES
⚠️ Notes: Module uses tuple-based returns, not objects

✅ Ready for skill generation with /generate-cpan-skill
```

## Error Cases

If the module doesn't exist or has issues:
- ❌ Module not found on MetaCPAN
- ⚠️ Module documentation incomplete
- ⚠️ Module deprecated or abandoned
- 💡 Suggestions for similar modules