# How to use the Plugin

The following are a couple of notes of the behavior of the plugin that might be different from what someone is used to.

## Subscriptions and Closing Behavior

Due to the callback nature of the Dolphin Scripting Model, it's best to view a Request as a "Subscription" to an eventual response.
This is important because in a Frame-Advancing situation, you might be waiting several seconds if not minutes for a resposne.

If you close the underlying Connection, the current "Subscriptions" for the Socket will execute, but fail to return.

This means if you have a pending "Write" operation, but close your connection, ***that write will happen***,
there will be no way to prevent this as even the Plugin is "subscribed" to the action, so after the request is made that
action is queued in Dolphin Internally.

## Error Handling

An Error in the execution of the Request does not close the connecting socket. 