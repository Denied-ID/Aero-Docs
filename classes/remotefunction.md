# RemoteFunction

Calls the server from a client and waits for the answer.

A RemoteFunction works like a function call across the network. The client invokes it and blocks until the server's handler returns.

## Members

| Member | Type | What it does |
| --- | --- | --- |
| OnServerInvoke | function or nil | The handler. Assign it from a Script on the server. |
| InvokeServer | method | Client only. Calls the handler and returns its values. |

Assigning `OnServerInvoke` from a client raises `OnServerInvoke can only be assigned on the server`. Calling `InvokeServer` from the server raises `InvokeServer can only be called from the client`.

## Writing the handler

The handler receives the calling player first, then the arguments passed to `InvokeServer`:

```lua
remote.OnServerInvoke = function (player, ...)
    return ...
end
```

Whatever it returns comes back to the client as the return values of `InvokeServer`. An error raised inside the handler is raised at the caller.

The handler cannot yield. Waiting inside it raises `OnServerInvoke yielded; yielding inside OnServerInvoke is not supported yet` on the client.

There is no `InvokeClient` and no `OnClientInvoke`. A server that waited on a client could deadlock with a client that is already waiting on the server.

## Example

```lua
-- Script in ServerScriptService
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local buy = ReplicatedStorage:WaitForChild("Buy")

buy.OnServerInvoke = function (player, itemId)
    if itemId == "sword" then
        return true, "bought"
    end

    return false, "unknown item"
end
```

```lua
-- LocalScript
local ReplicatedStorage = game:GetService("ReplicatedStorage")
local buy = ReplicatedStorage:WaitForChild("Buy")

local ok, message = buy:InvokeServer("sword")
print(ok, message)    -- true, bought
```

## See also

- [RemoteEvent](remoteevent.md): messages that do not wait for an answer.
- [Client and server](../scripting/client-and-server.md): the model this call crosses.
- [Instance](../globals/instance.md): the shared members.
- [API Reference](../api/api.md)
