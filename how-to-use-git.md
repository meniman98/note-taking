# Using git

## Going back in commits

### revert

The revert is an action that lets you go back in commits and start over, without discarding any progress you made.

When is it useful? Suppose you developed something and you aren't fully satisfied, maybe another implementation would've been better. You're doubtful.
A good idea would be to start over, without discarding any progress you made. 
You get to develop a new solution, and you'll have the ability to compare your old solution to your new solution and decide which is best

### reset

The reset is an action that lets you go back to whatever commit in the past while discarding all its child commits.

When is it useful? Resets are dangerous because child commits will be discarded; if you've developed something that you definitely don't want, then you can do a reset.
You must be sure

### drop

The drop acts almost like a delete action, it can remove a commit like it never existed

When is it useful? I'm still trying to figure this one out because I never ran into a situation where I wanted to drop a commit

### undo

Undoing a commit is like doing ctrl+z on a commit: your commit will be undone. This only works on the newest commit

When is it useful? An undo is useful if you've made a commit that you don't want

### rebasing

Rebasing is an action where you revisit a commit from the past. Useful for when you want to see code from an older commit. You are then 
able to experiment by making new commits from the new HEAD. However, your new commits will be discarded when you rebase back to MASTER

When is it useful? When you want to look back on how you implemented something, and optionally implement something new as an experiment

