# bash/zsh completion support for core Git.

 The contained completion routines provide support for completing:

    *) local and remote branch names
    *) local and remote tag names
    *) .git/remotes file names
    *) git 'subcommands'
    *) git email aliases for git-send-email
    *) tree paths within 'ref:path/to/file' expressions
    *) file paths within current working directory and index
    *) common --long-options

 To use these routines:

    1) Copy this file to somewhere (e.g. ~/.git-completion.bash).
    2) Add the following line to your .bashrc/.zshrc:
        source ~/.git-completion.bash
    3) Consider changing your PS1 to also show the current branch,
       see git-prompt.sh for details.

 If you use complex aliases of form '!f() { ... }; f', you can use the null
 command ':' as the first command in the function body to declare the desired
 completion style.  For example '!f() { : git commit ; ... }; f' will
 tell the completion to use commit completion.  This also works with aliases
 of form "!sh -c '...'".  For example, "!sh -c ': git commit ; ... '".

 If you have a command that is not part of git, but you would still
 like completion, you can use __git_complete:

   __git_complete gl git_log

 Or if it's a main command (i.e. git or gitk):

   __git_complete gk gitk

 Compatible with bash 3.2.57.

 You can set the following environment variables to influence the behavior of
 the completion routines:

   GIT_COMPLETION_CHECKOUT_NO_GUESS

     When set to "1", do not include "DWIM" suggestions in git-checkout
     and git-switch completion (e.g., completing "foo" when "origin/foo"
     exists).

   GIT_COMPLETION_SHOW_ALL_COMMANDS

     When set to "1" suggest all commands, including plumbing commands
     which are hidden by default (e.g. "cat-file" on "git ca<TAB>").

   GIT_COMPLETION_SHOW_ALL

     When set to "1" suggest all options, including options which are
     typically hidden (e.g. '--allow-empty' for 'git commit').
