# sudo / su

> `su` stands for superuser; that is, a user that can perform actions restricted to typical users. This is the underpinning of any commands with the `su*` prefix

By default, many Unix-like operating systems have a *superuser* or *root user* account that can perform *restricted / elevated* actions. The typical pattern is that a user has a non-root / "non-superuser" account they use for most things, but the superuser is invoked when needed by those who have permission.

## sudo

`sudo` means "*do*" something as the superuser. Command temporarily elevates current user to *superuser* do perform an elevated action (for instance, updating packages on a machine)

## su

`su -`

> *become* the superuser for the duration of the shell session


`su {someuser}`

> *become* {someuser} for the duration of the shell session