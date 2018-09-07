<!-- TITLE: Reverse Engineering Function Purpose -->
<!-- SUBTITLE: A quick summary of Reverse Engineering Function Purpose -->

# Goals
The primary goal of working out the purpose of a function is to understand an application in discrete chunks.  Applications are made of collections of functions. If you fully understand all of the functions of an application then you should be able to say you understand the entire application.  Rarely is this actually required though.  Most often you only need to understand a handful of code paths (and their associated basic blocks) to gain a working understanding of an application.  

# Setup
When an application first starts there is usually initialization that needs to take place.  Basic data structures need to be initialized.  Connections to data sources may need to be established.  Saved State (from a previous session) might need to be loaded.  Understanding this can be useful to a reverse engineer, but it's rarely key.  In general, the security of a piece of software isn't considered "compromised" if a local user can effect how the application is loaded.  A user can always compromise themselves.

The exception would be if things like credentials are stored by the application and then loaded during setup.  These credentials may well be the keys that allow a tester to compromise the server environment.  They may also have dire consequences for the client environment if for example administrator credentials are stored locally and then re-used. 

# Main Loop
There is almost always some sort of "Primary Loop" or event handler that an application will use.