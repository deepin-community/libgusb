GUsb
====

GUsb is a GObject wrapper for libusb1 that makes it easy to do
asynchronous control, bulk and interrupt transfers with proper
cancellation and integration into a mainloop.
This makes it easy to integrate low level USB transfers with your
high-level application or system daemon.

Not everything you can do in libusb1 is wrapped, although we'll accept
feature requests (with patches) if it makes sense.
