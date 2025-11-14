---
name: result-simple-perl
description: Use Result::Simple for tuple-based error handling in Perl
version: 1.0.0
author: kfly8
tags: [perl, cpan, error-handling, result-type]
---

# Result::Simple - Tuple-based Error Handling

Result::Simple provides lightweight error handling using tuples `($value, $error)` instead of objects.

## Core Functions

### `ok($value)` / `err($error)`
```perl
use Result::Simple qw(ok err);

sub divide {
    my ($a, $b) = @_;
    return err('Division by zero') if $b == 0;
    return ok($a / $b);
}

my ($result, $error) = divide(10, 2);
if ($error) {
    warn "Error: $error";
} else {
    print "Result: $result";
}
```

## Practical Examples

### Error Chaining Pattern
```perl
sub process_config {
    my $filename = shift;
    
    my ($content, $read_error) = read_file($filename);
    return (undef, $read_error) if $read_error;
    
    my $data = eval { decode_json($content) };
    return err("JSON error: $@") if $@;
    
    return ok($data);
}
```

### Type Checking
```perl
use Result::Simple qw(result_for);

sub calculate {
    my ($a, $b) = @_;
    return err('Invalid input') if $a < 0;
    return ok($a * $b);
}

result_for calculate => 'Num', 'Str';  # Enable type checking
# Set RESULT_SIMPLE_CHECK_ENABLED=1 to activate
```

