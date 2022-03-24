# metamodel-lua

a lua DSL useful to construct petri-net state machines

## Usage

This library is a very simple implementation.
It's recommended to simply add this lua file to your own project.

https://raw.githubusercontent.com/pFlow-dev/metamodel-lua/master/src/metamodel.lua


### Examples

A simple demo of the DSL
See tic-tac-toe example for a more complex model.

```
domodel("counter", function (fn, cell, role)
	local user = role("user")

	local p0 = cell('p0', 1, 0, {x=1,y=0})
	local inc0 = fn('inc0', user, {x=1, y=1})
	inc0.tx(1, p0)
	local dec0 = fn('dec0', user, {x=1, y=1})
	p0.tx(1, dec0)

	local p1 = cell('p1', 0, 1, {x=1,y=1})
	local inc1 = fn('inc1', user, {x=1, y=2})
	inc1.tx(1, p1)
	local dec1 = fn('dec0', user, {x=1, y=1})
	p1.tx(1, dec1)

	local p2 = cell('p2', 0, 1, {x=1,y=3})
	p2.guard(1, inc0)
	local inc2 = fn('inc2', user, {x=1, y=3})
	inc2.tx(1, p2)
	dec2 = fn('dec2', user)
	p2.tx(1, dec2)
end)
````
