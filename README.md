git-asana-post-commit-hook
==========================

Git hook for Asana that updates tasks when commits are made.

http://www.asana.com

Installation
============
You need need to set your Asana API key in your git configuration settings.

	git config asana.key {your-api-key} 

	or

	git config --global asana.key {your-api-key}

Then install the post-commit file to your .git/hooks directory.  If there's a problem with your setup it will be displayed to you when you commit the next time.

[Asana API Key]: http://developer.asana.com/documentation/#api_keys

Commit Syntax
=============
When committing, use one of the following verbs followed by an Asana task ID in your commit message (prefixed by a #):

*To mark a task as complete*
    Fix
    Fixes
    Fixed
    Fixing
    Close
    Closes
    Closed
    Closing

*To only reference a task*
    Addresses
    Addressing
    References
    Referencing
    Refs
    Ref
    Re
    See

*To mark a task as incomplete*
    Breaks
    Breaking
    Unfixes
    Unfixing
    Reopen
    Reopening
    Reopens
    Re-open
    Re-opens
    Re-opening

Commit messages may reference multiple task IDs:

    git commit -m "Fixed #123456789, breaks #5551212. References #3241"
    
Commit messages may also use any combination and order of verb and IDs...

    git commit -m "This fixed a few problems in #123,#456, and #555, also breaking #7 and #2. I suppose I should reference #99 and #98"

...as long as a verb comes before any IDs.

    git commit -m "I think #22 and #23 should be referenced" (This will not work)

The commit message will be attached to any referenced task ID, regardless of verbs or order.

The end of any sentence resets any verbs used earlier in the sentence:

    git commit -m "Fixed #123123, breaks #999. I should mention #7 too." (#7 is not broken like #999; it only receives a comment)

Task IDs in Asana are the strings of digits after the final slash in the url, visible when you're viewing a task.