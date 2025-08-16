# Digosaurs

You can add a new digosaur like this:
```lua
local name = "my-new-digosaur"
local bonus = 2
local proxy_name = "my-nex-digosaur-proxy"
remote.call("py_digosaurs", "new_digosaur", name, bonus, proxy_name)
```

You can also remove existing digosaurs like so:
```lua
remote.call("py_digosaurs", "remove_digosaur", "digosaurus")
```
