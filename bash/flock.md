# `flock`

Linux [has](https://linux.die.net/man/1/flock) a `flock` command to
manage file locks from shell scripts.

One example from [https://linuxaria.com/](https://linuxaria.com/howto/linux-shell-introduction-to-flock)
is to lock a file in a script and allow it to automatically go out of
scope and release itself when the file
gets closed.

```bash
#!/bin/bash

lock="/var/run/file"

# exec can also be used to open a file and name a file handle for it.
# The call exec 200>"${lock}" will open the file named in $lock for reading
# and assign it file descriptor 200.
exec 200>"${lock}"
# This tells flock to exclusively lock the file referenced by file handle 200
# or exit with code 1.
# The state of being locked lasts after the flock call because the file
# handle is still valid.
# That state will last until the file handle is closed - in this case until
# the script exits.
flock -n 200 || exit 1
```
