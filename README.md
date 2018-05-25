# git-gff
git file filter

This script will list files from git status that meet criteria you specify.

```
The default, with no options is -? which is unknown files. (Those not currently tracked in git)
-m all modified files
-mw files that have modifications in the working tree
-mi files that have modifications staged in the index
-d files that are deleted
-dw files deleted from the working tree
-di files staged for deletion in the index
-a new files that are staged in the index
```

My thoughts are to add a set of arguments for the seperator, (like -print0 from find), and to set if the full path is output, or just the path from the index base.

The biggest limitation at this point is that the script does not handle and filename in which a character needs escaping.  This includes spaces.  I have worked and worked, and failed at this point.

### Use cases:

You can just type gff and get a list of files that are unknown but thats not a lot better then git status --short.  My thoughts were that it will also to allow something like this: 
```
tar cf archive.tar $(gff)
```
to tar all files that are unknown to git.  Or 
```
mv $(gff -mw) somewhere
```
which would move any file modified in the working tree to somewhere.  Or anything else you can think of (rm, grep, etc).

I'd welcome suggestions or pull requests as long as they fit the vision of a simple script to make it easier to work with files classified by git status.  And obviously if you can help with the command substitution problem, I'd love to learn how it should be done.
