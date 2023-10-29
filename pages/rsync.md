# Rsync

`rsync` is a fast, powerful, highly versatile tool for synchronizing files between directories. These directories can both be on the same machine, but usually, one is on the local machine, another is somewhere else.

If rsync is employed as a remote backup tool, and should something happen to the local machine (corruption, theft, destruction), all files will be saved as perfect copies on the remote machine, to be retrieved again.

## Example usage and explanation of used flags

```bash
[sudo] rsync -avzn -e 'ssh -p PORT' --human-readable --progress --stats --delete /home/localuser/Videos/ remoteuser@IP:/home/remoteuser/Videos/
```

> sudo *may* be necessary
> > **-avzn -e**
> >
> > > -a : a flag that actually contains / runs many *other* flags (-rlptgoD). Consider this the 'default' way to run rsync that you'll always want to run until you learn more about the program
> > >
> > > -v : 'verbose'; write more information to the terminal while command occurs
> > >
> > > -z : compress the data while transferring
> > >
> > > -n : 'dry-run'; show what will happen without performing the action; if the action looks good, user removes this flag and actually runs the command
> > >
> > > -e : tells rsync an *expression* will follow (see next section)...
> >
> > **ssh -p PORT**
> >
> > > ssh : the 'ssh' command. tells rsync to invoke it
> > >
> > > -p : PORT
> > >
> >
> > **--human-readable --progress --stats --delete**
> > >
> > > --human-readable : report sizes in human-readable formats (e.g. gigabytes, megabytes, etc.)
> > >
> > > --progress: show progress during transfer
> > >
> > > --stats: show stats at end of a dry-run or transfer; show summary of what happened / will happen
> > >
> > > --delete: don't just add new files to the destination; also *remove* files from the destination that aren't in the source location on the local machine. This long option ensures the two direcgtories are perfect copies
> >

## A Simpler Example with Two Local Directories

```bash
rsync -avzn --delete /home/localuser/Videos/ /home/localuser/VideoBackups/
```

## Utility

Why use rsync, even if your backup is on the same machine?

- rsync is faster is almost all cases
- if failure occurs before command completion, rsync can pick up where it left off if you run the command again. This can't be said for simply copying a directory to another location
- rsync is intelligent and makes *differential backups*; that is, if you are syncing two directories that are very large, it will not rewrite unchanged files existing on both machines already. It will only make changes where necessary to harmonize the two directories, until they are identical (assuming you use the `--delete` long option)