# Events

## Working with Bukkit Events

Of course, you can also use Bukkit's events. To register an event listener, use the `#!kotlin Listener.registerEvents()`
extension function.

## Working with Packet Events

You can also listen to incoming and outgoing packets.
To do so, implement the `PacketListener` interface and register your listener using the
`#!kotlin PacketListener.registerPacketHandler()` extension function.
Then, you can use the `#!kotlin @PacketHandler` annotation to mark event methods.

!!! abstract "Packet Event Types"

    Please note that this currently does not include all possible packets, as the system is still in development.
    Feel free to open an issue or a pull request if you need another packet type.

## Calling events from Nova's Plugin API

You might've noticed that the `nova-api` module is not in your classpath. This module is explicitly for developers of
third party plugins and provides a stable API for Nova. To prevent addon developers from accidentally using those
classes, `nova-api` is not a transitive dependency of `nova`.

To still call events from Nova's Plugin API, use the `NovaEventFactory`:

```kotlin
// obtain drops from the block
val drops: MutableList<ItemStack> = block.getAllDrops().toMutableList()
// call the event (might mutate drops list)
NovaEventFactory.callTileEntityBlockBreakEvent(this, block, drops)
```
