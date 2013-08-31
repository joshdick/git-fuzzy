# git-fuzzy

Makes Git a little fuzzier.

_by [Josh Dick](http://joshdick.net)_

## Install It

    npm install -g git-fuzzy

## Use It

Installing `git-fuzzy` should have made it available on your `$PATH`.

`git-fuzzy` is a wrapper for Git at the command line. Use Git just like you normally would, except prefix your Git arguments with "fuzzy".

If the last argument looks like a filename, `git-fuzzy` will attempt to fuzzy match it to the name of a file that has been modified in the working directory of your Git repository. Otherwise, `git-fuzzy` will just pass your Git arguments through to Git, unmodified.

For example:

    > git status
    # On branch master
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    #	modified:   another/very/long/path/myawesomefile.ext
    #	modified:   some/really/long/path/anotherfile.ext
    #
    no changes added to commit (use "git add" and/or "git commit -a")

    > git fuzzy add awesome

    > git status
    # On branch master
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #	modified:   another/very/long/path/myawesomefile.ext
    #
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #
    # modified:   some/really/long/path/anotherfile.ext
    #

Typical uses of `git-fuzzy` include things like:

    > git fuzzy add somefile

    > git fuzzy reset HEAD somefile

    > git fuzzy checkout somefile

## To Do

* Attempt to fuzzy-match against [tree-ish](https://www.kernel.org/pub/software/scm/git/docs/)es in addition to filenames.
* Attempt to fuzzy-match against all files in the repository, instead of just those that were modified in the working directory.
* Attempt to fuzzy-match exact paths, since `git-fuzzy` treats these as ambiguous.
* Attempt to fuzzy-match against multiple arguments, or at least arguments other than the last one.

## Disclaimer

I take no responsibility if `git-fuzzy` does unexpected or destructive things to your computer or Git repository. Use it at your own risk. It Works For Me™.

## License

`git-fuzzy` is copyright (c) Joshua Dick, and is licensed under the [MIT license](http://opensource.org/licenses/MIT). `git-fuzzy` depends on [`fuzzy`](https://github.com/mattyork/fuzzy), which is released under the same license.
