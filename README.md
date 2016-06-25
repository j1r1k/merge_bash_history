# merge-bash-history

Utility to be used with unison (http://www.cis.upenn.edu/~bcpierce/unison/) to merge `.bash_history` file accross multiple machines.

# Installation

Clone the repository

```
git clone https://github.com/j1r1k/merge-bash-history.git
```

Install using stack
```
cd merge-bash-history
stack install
```

# Example configuration in unison preferences file

Assuming you have root set to your home directory and `merge-bash-history` is in your $PATH

Add following to your unsion .prf file

```
merge = Name .bash_history -> merge-bash-history CURRENT1 CURRENT2 > NEW
backupcurrent = Name .bash_history
```

# Manual usage

```
merge-bash-history [INPUT-FILE1] [INPUT-FILE2] > [MERGED-FILE]
```

# Limitations
- Does not support line deletion (e.g. manual removal of lines from .bash_history file)

# Warnings
- Sorts .bash_history file by timestamp if not sorted
- removes duplicates (comparing timestamp and command)

# Recommended Bash settings

```
shopt -s histappend
PROMPT_COMMAND="${PROMPT_COMMAND};history -a"
```

From Pawel Hajdan (http://phajdan-jr.blogspot.de/2015/03/more-reliable-handling-of-bash-history.html)
