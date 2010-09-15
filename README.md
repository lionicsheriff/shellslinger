USAGE
=====
    Usage: sling [options] [files]
      --commands, -c:   Show commands
          --keys, -k:   Show keys
          --help, -h:   Show this message

Sling will zip through the files applying commands as fast as you can type.

CONFIG
======

Configuration is kept in ~/.slingrc

##Format

    ---
    :keys:
        key bindings go here
    :filetypes:
        file handlers go here
    :abbrev:
        abbreviations go here

##Keys

###Format 

    s: shell command
    i: :internal_command
    m:
        m: command
        a: another command
    l: - Label
       - command

##Filetypes

File types are used in the preview command. 

###Format

    extension: handler
    can,have,many,extensions: handler can use %escapes

##Abbreviations

Abbreviations are custom escapes. 

###Format

    name: replacement text

COMMANDS
========

##Modifiers

###Prefixes

**:** denotes an internal command

**<** at the start of a shell command stops it from being put into command history.

##Suffixes 

**!** at the end of a shell command will add it to the command queue to be processed when you are finished with the file. Queued commands can be removed with the :undo internal command.

**?** at the end of a shell command will cause sling to ask for confirmation before processing the command.

ESCAPES
=======

Current escape sequences for commands are

    %f                  Current file
    %i                  Read user input
    %%                  Literal %

Entries in the abbrev section of the config are escaped with %abbrev_name. The escapes are parsed in this order %i > %abbrev > %i > %f.

INTERNAL COMMANDS
=================

Commands are prefixed with ':' when making a map

    show_queue          Show commands queued for this file
    config_load         Reload configuration file
    exit                Quit this program
    enter               Enter directory
    next                Next file
    show_prev_cmd       Show previous command on file
    preview             Preview file
    config_save         Save configuration
    undo                Remove most recent item from queue
    keys                Show key bindings
    map                 Map new command
    prev_cmd            Repeat previous command on file
    enqueue             Put next command into queue
    do_action           Do an action from input

Everything else is evaluated in the shell
