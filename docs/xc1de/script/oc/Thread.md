# Function OC/Object

---

## Constructor

`oc thread(function entrypoint, string name = "")`

Creates a new thread.

---

## Methods

### start

`void thread->start()`

Starts the thread.

### end

`void thread->end()`

Ends the thread.

### isAlive

`bool thread->isAlive()`

Returns whether the thread is alive/active.

### join

`void thread->join()`

Waits until the thread terminates.

### sleep

`bool thread->sleep()`

Puts the thread to sleep.

### wakeup

`bool thread->wakeup()`

Wakes up the thread.