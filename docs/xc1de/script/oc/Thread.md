# Function OC/Object

---

## :material-new-box: Constructor

`oc thread(function entrypoint, string name = "")`

Creates a new thread.

---


## Methods

### :material-function: start

`void thread->start()`

Starts the thread.

---

### :material-function: end

`void thread->end()`

Ends the thread.

---

### :material-function: isAlive

`bool thread->isAlive()`

Returns whether the thread is alive/active.

---

### :material-function: join

`void thread->join()`

Waits until the thread terminates.

---

### :material-function: sleep

`bool thread->sleep()`

Puts the thread to sleep.

---

### :material-function: wakeup

`bool thread->wakeup()`

Wakes up the thread.