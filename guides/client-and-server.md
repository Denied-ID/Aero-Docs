# Client and server

Where code runs, and what travels between the two sides.

A place runs as a server with clients attached. The server loads the place, simulates the world, and sends every change to the clients. Each client renders what it receives and runs its own scripts. One place, two views.

## Which script runs where

| Class | Runs on | Typical home |
| --- | --- | --- |
| [Script](../classes/script.md) | the server | [ServerScriptService](../services/serverscriptservice.md), Workspace |
| [LocalScript](../classes/localscript.md) | one client | [StarterPlayer](../services/starterplayer.md), [StarterGui](../services/startergui.md) |
| [ModuleScript](../classes/modulescript.md) | whichever side requires it first | [ReplicatedStorage](../services/replicatedstorage.md) |

A script can ask where it is:

```lua
local RunService = game:GetService("RunService")

if RunService:IsServer() then
    print("the server half")
else
    print("a client half")
end
```

## What each side sees

- The server sees the whole tree, including [ServerScriptService](../services/serverscriptservice.md), which clients never receive.
- [ReplicatedStorage](../services/replicatedstorage.md) reaches both sides: the same instances at the same paths, which is what makes it the home for shared modules and remotes.
- [StarterGui](../services/startergui.md) and [StarterPack](../services/starterpack.md) are templates. Each joining player gets copies in their own PlayerGui and Backpack, and the copy is what runs.
- A client's copy belongs to that client. A change a client script makes stays on that client; the server learns nothing until a script tells it.

## Crossing the gap

| You want | Use |
| --- | --- |
| a message, either direction | [RemoteEvent](../classes/remoteevent.md) |
| an answer the client waits for | [RemoteFunction](../classes/remotefunction.md) |

A remote carries data, not authority. The server decides what a message means, and a client cannot change the world everyone shares except by asking.

The [RemoteEvent](../classes/remoteevent.md) page shows the pair of scripts that pass a message from a client to the server and back.

## See also

- [Script](../classes/script.md) and [LocalScript](../classes/localscript.md): the two classes and where they start.
- [Player input](player-input.md): keys and clicks on the client half.
- [Scripting best practices](scripting-best-practices.md): the habits this model rewards.
- [Testing your place](../tutorials/testing-your-place.md): both halves running in one Studio process.
- [API Reference](../api/index.md)
