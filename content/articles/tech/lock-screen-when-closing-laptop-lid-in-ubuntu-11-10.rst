Lock screen when closing laptop lid in Ubuntu 11.10
###################################################
:date: 2012-02-13 13:03
:tags: ubuntu
:slug: lock-screen-when-closing-laptop-lid-in-ubuntu-11-10


An useful thing to do is to have lock the screen when you close the laptop lid so you don't have to wait for the timeout but in Ubuntu 11.10 this feature was disabled.

*Note: This bug has been fixed in Ubuntu 12.04 Precise Pangolin.*

To have your screen locked when you close your lid under Ubuntu 11.10 you need to edit ``/etc/acpi/lid.sh`` and just after the line

.. code-block:: bash

    . /usr/share/acpi-support/screenblank

add the following line:

.. code-block:: console

    su $user -c '/usr/bin/gnome-screensaver-command -l'


So the result should look something like:

.. code-block:: bash

    [...]
        for x in /tmp/.X11-unix/*; do
            displaynum=`echo $x | sed s#/tmp/.X11-unix/X##`
            getXuser;
            if [ x"$XAUTHORITY" != x"" ]; then
                export DISPLAY=":$displaynum"
                . /usr/share/acpi-support/screenblank
                su $user -c '/usr/bin/gnome-screensaver-command -l'
            fi
        done
    [...]

