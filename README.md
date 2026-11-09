# Scoped Variables

Access variables in a namespace derived from the current script, its folder, or an explicitly selected script. This helps keep otherwise similarly named variables separate between scripts or packages.

## Requirements

- Skript 2.15+
- skript-reflect 2.6+

## Installation

```
package install https://github.com/devdinc/scoped-variables
```

## Syntax

```skript
scoped %objects%
scoped %objects% in %script%
scoped %objects% in current folder
```

The expression supports reading and the standard variable changes: set, add, remove, remove all, delete, and reset.

### Default scope

Set the default scope for variables used in the current script:

```skript
set default scope for scoped variables in current script to current folder
set default scope for scoped variables in current script to current package
set default scope for scoped variables in current script to current script
set default scope for scoped variables in current script to folder "systems"
set default scope for scoped variables in current script to package "my-package"
set default scope for scoped variables in current script to script "combat.sk"
```

The current script is the default when no explicit default scope has been configured. The current folder scope is based on the script's path relative to the server's Skript scripts folder.

## Examples

```skript
# Uses the current script's configured/default scope
set scoped {_score} to 10
add 5 to scoped {_score}
broadcast "%scoped {_score}%"

# Use a particular script's scope
set scoped {_enabled} in script "combat.sk" to true

# Use the folder containing the current script
delete scoped {_temporary} in current folder
```

Local and ephemeral variable types retain their corresponding variable prefixes inside the scoped namespace.

## Dependencies

This package depends on [event-specified-variables](https://github.com/devdinc/event-specified-variables).

## Source and tests

- Implementation: `src/scoped-variables.sk`
- Tests: `-tests/`
