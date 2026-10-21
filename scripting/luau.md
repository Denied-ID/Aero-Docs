# The Luau standard library

What the VM provides, on top of the engine's own API.

Scripts on Aero are Luau scripts. Besides `game`, `Instance`, and everything else in the [API reference](../api/index.md), the VM ships a standard library of its own. This page lists what is available and where the engine has narrowed it. The Luau site, [luau.org](https://luau.org/), documents each function.

## Libraries

| Library | What it holds |
| --- | --- |
| string | Text handling: lengths, casing, patterns, formatting. |
| table | Arrays and dictionaries: insert, remove, sort, freeze. |
| math | Constants and functions, including `math.random`. |
| os | `clock`, `date`, `difftime`, and `time`. |
| coroutine | Threads: create, resume, yield, status. |
| buffer | Fixed-size binary buffers. |
| bit32 | Bitwise operations on 32-bit integers. |
| utf8 | UTF-8 encoding and decoding. |

`os` is the narrowed one. Only the four functions above exist. There is no `io`, and no way for a script to reach files, processes, or environment variables.

`vector` builds Luau's native vector type. It is separate from the engine's [Vector3](../globals/vector3.md): every property and method in the reference takes Vector3, and nothing in Aero hands a script a native `vector`.

## debug is removed

Luau ships a `debug` library that reaches around the language: upvalues, hooks, tracebacks of other threads. The engine removes it before any script runs, so reading `debug` returns `nil`. [Perf](../services/perf.md) is the supported way to inspect what a script costs.

## Base functions

The base globals are Luau's own: `assert`, `error`, `pcall`, `xpcall`, `pairs`, `ipairs`, `next`, `select`, `unpack`, `tonumber`, `tostring`, `type`, [typeof](../functions/typeof.md), `setmetatable`, `getmetatable`, `rawget`, `rawset`, `rawequal`, `rawlen`, `setfenv`, and `getfenv`. Two older names ride along: `gcinfo` and `newproxy`.

`_G` is the globals table and `_VERSION` is the string `Luau`.

## The run budget

A script that runs too long without yielding is stopped. A single uninterrupted run past five seconds raises `Script exceeded its run budget`. Yielding ends a run: `task.wait`, `WaitForChild`, and a signal's `Wait` hand control back, and the thread starts a fresh budget when it resumes.

## See also

- [typeof](../functions/typeof.md): names a value's type.
- [task](../functions/task.md): Aero's scheduler, built on the same threads.
- [API Reference](../api/index.md)
