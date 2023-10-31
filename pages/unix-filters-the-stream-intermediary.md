# Interactive Unix Filters

In UNIX, ["everything is a file"](EIAF.md), and we manage all these files (real, virtual, and otherwise) with [streams](anatomy-of-input-output-and-other-streams.md) and [pipes](pipes.md).

Streams and pipes are very simple, yet powerful; for any type of programmatic action with a clear pattern of scope that we wish to operate on (e.g. all files that have a ".txt" extension, or all files in a directory that contain some certain word), it's easy to write scripts or on-the-fly interactive commands to achieve what we wish: the logic is **concrete**.

What, then, do we do when the logic is *fuzzy*, and we wish to select files / folders *arbitrarily*, or based on parameters known to us, but hard to describe with precise shell commands? In these cases, we employ a <mark>UNIX Filter</mark>; with modern Unices, we can employ powerful UNIX filters like <mark>fzf</mark> that are *visual*, *interactive*, and *robust* through their adherence to simple principles.

Interactive UNIX filters (also called 'fuzzy finders' or 'fuzzy pickers' sometimes) are a highly flexible broker between `stdin` and `stdout`; they are not native to common Unices, but are, in the author's opinion, sufficiently useful, principled, and *generic* to be considered as essential to the command-line toolkit as other native shell tools and [core utilities](core-utils.md); a *missing ingredient*, if you will. Explore the details of how they work on the [fzf](fzf.md) page.
