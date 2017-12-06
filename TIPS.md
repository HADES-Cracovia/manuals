Tips
====

Prepare ssh
-----------

In your `~/.ssh/config`

    Host                        gsi
        Hostname                lx-pool.gsi.de
        Port                    22
        User                    your_user_name
        ForwardAgent            yes
        ForwardX11Trusted       yes
        TCPKeepAlive            yes
    
    Host                        kro
        User                    your_user_name
        ProxyCommand            ssh -q gsi -W kronos.hpc.gsi.de:%p

Replace `your_user_name` with your GSI user name.

Now you can connect to GSI machine using `ssh gsi -Y` or to farm machines using `ssh kro -Y`. Always use `-Y` parameter i ncase you will need X server.


Prepare environment
--------------------

Go to kronos computer `ssh kro -Y`

Create hades work dir

    mkdir ~/hades/pp45
    cd hades/pp45

(for proton+proton 4.5 GeV, for different energies you can create different names).

Make some subdirs for more organization.

    mkdir sim

Go to lustre (see Tips on the end of this file). On lustre make:

    mkdir hades/pp45 -p

Prepare profile
---------------

You must have a profile script. If not yet, you can use an example from this repository

    cp profile.sh.example ../../profile.sh

and edit the file woth your favorite editor to adjust `HADDIR` (if using custom hydra) and `HGEANT_DIR` variables.

Quick lustre access
-------------------

in your `~/.bash.rc` add these lines to easy access lustre

    function lustre {
        cd /lustre/nyx/hades/user/${USER}
    }

Then is enough to type `lustre` in your cmd to go there, to get back home type `cd`.

You must reload your profile to apply these changes, execute

    . ~/.bash.rc

Working with git
----------------

To clone repository

    git clone address destination

After you made changes, commit them to the repository

    git commit -m "Message text" -a

If you use switch `-a` then all changes are commited, if you wanna commit only selected files, put file names instead of `-a`.

    git push

will push the data to remote repository.

If you want to fetch recent changes from the repository

    git pull

All these actions you must do inside the repository directory: the `destination` parameter of the clone directory.
