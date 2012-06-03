words
=====

This is an import of William Whitaker's WORDS Version 1.97FC LATIN-ENGLISH
DICTIONARY PROGRAM.

using
-----

I don't know how to use `words` yet.  It probably isn't too hard,
though.

building
--------

words is written in Ada, which might be a problem.  Most Linux distros
have gnat packages available.  On OSX I've been using Ada compiler
binaries that I downloaded from
http://libre.adacore.com/download/configurations and, still in OSX, I frob
`$PATH` with the following, which I have added to my bash configuration files.

    # ada crap
    IN_GNAT=0
    PRE_GNAT_PATH=
    PRE_GNAT_PS1=
    function load_gnat () {
        if [ $IN_GNAT -ne 0 ] ; then
            echo "Aready in gnat mode."
            return
        fi
        echo -n "Configuring gnat... "
        GNAT=~/local/gnat/bin
        PRE_GNAT_PATH=$PATH
        PRE_GNAT_PS1=$PS1
        export IN_GNAT=1
        export PS1="[gnat] $PS1"
        export PATH=$GNAT:$PATH
        echo "done."
    }
    
    function unload_gnat () {
        echo -n "Unconfiguring gnat... "
        if [ $IN_GNAT -ne 1 ] ; then
            echo "wasn't in gnat mode in the first" 'place!'
            return
        fi
        export IN_GNAT=0
        export PATH=$PRE_GNAT_PATH
        export PS1=$PRE_GNAT_PS1
        echo "done."
    }
    