# require

Loads a ModuleScript and returns what it returned.

`require` runs a ModuleScript the first time you call it and hands back the module's return value. Later calls return the cached value, so the body of a module runs once per script VM, no matter how many scripts require it.

## Signature

| Call | Returns |
| --- | --- |
| `require(module)` | whatever the module returned |

The argument must be a ModuleScript instance. Passing anything else raises an error.

## What a module must do

A module has to return a value. The value can be anything: a table of functions, a single function, a number, or an Instance.

| Situation | Result |
| --- | --- |
| The module returns a value | `require` returns it, and caches it. |
| The module returns nothing or `nil` | Error: `Module 'ReplicatedStorage.MathUtil' did not return anything` |
| Two modules require each other | Error: `cyclic require of 'ReplicatedStorage.MathUtil'` |
| The module raises an error | The error reaches the caller, reported against the module's own path. |

The error text uses the instance's full name, which is why the path appears in it.

## Example

```lua
-- ModuleScript in ReplicatedStorage, named MathUtil
local MathUtil = {}

function MathUtil.clamp(value, low, high)
    return math.max(low, math.min(high, value))
end

return MathUtil
```

```lua
-- Script
local MathUtil = require(game:GetService("ReplicatedStorage").MathUtil)
print(MathUtil.clamp(12, 0, 10))    -- 10
```

## See also

- [ModuleScript](../classes/modulescript.md): the instance `require` reads.
- [Instance](../globals/instance.md): how to find the module in the tree.
- [API Reference](../api/api.md)
