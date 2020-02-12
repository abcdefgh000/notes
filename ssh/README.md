## Trouble Shooting

When running `ssh 111.222.111.222`, if seeing some error similar to this:
```
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the ECDSA key sent by the remote host is
SHA256:blablabla...
Please contact your system administrator.
Add correct host key in /Users/baby/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /Users/baby/.ssh/known_hosts:1
ECDSA host key for 111.222.111.222 has changed and you have requested strict checking.
Host key verification failed.
```

Run this cmd to reset :
```
$ ssh-keygen -R 111.222.111.222
# Host 111.222.111.222 found: line 1
/Users/baby/.ssh/known_hosts updated.
Original contents retained as /Users/baby/.ssh/known_hosts.old
```

Then use `ssh 111.222.111.222` again, this time it should work.
