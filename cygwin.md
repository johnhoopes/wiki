<!-- TITLE: Cygwin -->
<!-- SUBTITLE: A quick summary of Cygwin -->

# Installing Java in Cygwin
(from https://horstmann.com/articles/cygwin-tips.html)
Java

    Download and install the JDK in the usual way.
    Start the Cygwin shell from the Windows start menu.
    Open a Cygwin shell as a regular user. Run

    emacs .bash_profile &

    Add the following environment variable at the bottom of the file, before the export PATH statement:

    export JAVA_HOME=/cygdrive/c/Program\ Files/Java/jdkversion/

    where you should replace version with the version of your Java installation. Make sure to put a \ before each space in the path name. Then add $JAVA_HOME/bin to the path, like this:

    export PATH=$PATH:$EMACS_HOME/bin:$JAVA_HOME/bin

    Save the file.
    Run

    source .bash_profile
    javac -version

    That's javac, not java.

    If you get the correct version number, you are done.
