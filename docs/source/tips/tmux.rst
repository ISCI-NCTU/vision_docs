tmux & tmuxinator
=================

tmux
~~~~~
`tmux <https://tmux.github.io/>`_ is a powerful terminal multiplexer

What is a terminal multiplexer? It lets you switch easily between several
programs in one terminal, detach them (they keep running in the background) and
reattach them to a different terminal. And do a lot more.

.. image:: /_static/tmux.png
    :width: 500px
    :align: center

tmuxinator
~~~~~~~~~~

`tmuxinator <https://github.com/tmuxinator/tmuxinator>`_ is basically the best
way to configure tmux to make your life easier :)

With tmuxinator you can create and manage tmux sessions in yaml.

Installation instructions
~~~~~~~~~~~~~~~~~~~~~~~~~
tmux
----
To install tmux on your machine, just run the following command:

``sudo apt install tmux``


Then comes the hard part... You need to configure tmux the way you want it,
the way you like it.
You can change the binding keys, the theme, add several plugins,... There's a
lot of things you can add to your terminal to be more efficient.

For starters I recommend using the following configuration.

https://github.com/tony/tmux-config

It will change the key bindings to use `Ctrl+A` instead of `Ctrl+B` but also
add a cool theme and a cpu monitor to the terminals

Also to be able to use the mouse on the terminal, follow this tutorial:

http://tangledhelix.com/blog/2012/07/16/tmux-and-mouse-mode/

tmuxinator
----------
Follow the instructions on the github repository:

https://github.com/tmuxinator/tmuxinator

Help
~~~~

tmux commands
-------------

.. code-block:: python

  ctrl-a ?        help

  ctrl-a c        create a new window
  ctrl-a 1        switch to window 1, ..., 9, 0
  ctrl-a p        switch previous window
  ctrl-a p        switch next window
  ctrl-a w        switch to a window from a list

  ctrl-a "        split vertically
  ctrl-a %        split horizontally
  ctrl-a left     go to pane on the left
  ctrl-a right    go to pane on the right
  ctrl-a up       go to pane on the up
  ctrl-a down     go to pane on the down
  ctrl-a-left     resize left
  ctrl-a-right    resize right
  ctrl-a-up       resize up
  ctrl-a-down     resize down
  ctrl-a x        close current pane

  ctrl-a space    change the pane layout (tiled, main-horizontal, ...)

  ctrl-a &        kill window
  ctrl-a d        hide the tmux session and go back to the classic terminal

tmuxinator
----------
To create automatically an empty session run:

``mux new SESSION_NAME``

To start your session:

``mux SESSION_NAME``

Edit the session:

``mux open SESSION_NAME``

With tmuxinator you can specify you tmux in yaml like this

.. code-block:: bash

  name: kinect1_processing
  root: ~/

  windows:
    - WINDOW_NAME:
        layout: tiled    #even-vertical, even-horizontal
        panes:
          - roscore
          - htop
          - etc ...
    - WINDOW_NAME2:
        layout: main-horizontal   #main-vertical
        panes:
          - vi
          - etc ...

.. tip:: If you want to **only print** the command use : ``tmux send-keys -t SESSION_NAME:WINDOW_NAME.PANE_NB "command to print";``
