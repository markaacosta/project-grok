# Smart `cd`

Changing directories is a common task; sometimes directories are nested / consist of a long path that is tedious to type. Many tools exist to simplify the experience of changing directories; we'll explore `zoxide`, but concepts will be similar between it and potential alternatives.

## The 'what' of smart directory changing

Like [fuzzy file patterns](fzf.md) or [interactive recursive history retrievals](history.md#complex-fuzzy-retrievals), smart directory changing relies on fuzzy matching. Generally, a user visits a directory manually at least one time; in the future, a user can type only a unique *part* of that directory, and use a smart directory changer to move to it.

## zoxide: in practice

As a user (manually) visits directories, zoxide will begin keeping track of how often directories with similar paths are visited relative to other directories; internally, ranking is performed. After a while, a user will be able to immediately jump to a directory with `z {some_pattern}`, where `{some_pattern}` is a unique piece of an overall path.

![zoxide-basic](../assets/zoxide-basic.gif)

## graceful collision handling

When two paths are similar, the user may enter `z` \<space\>\<tab\> (don't forget the space) to resolve the ambiguity and select the correct directory:

![zoxide-collision-handling](../assets/zoxide-collision-handling.gif)