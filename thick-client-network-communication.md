<!-- TITLE: Thick Client Network Communication -->
<!-- SUBTITLE: A quick summary of Thick Client Network Communication -->

# Goals
Often the goal of watching network traffic is to gain access to the principal datasources that the application uses, without being hindered by the local client security controls.  For example a thick client might connect directly to a database.  The credentials, and connection information would be stored in the application.  By sniffing (and possibly [reverse-engineering](/reverse-engineering)) a tester might be able to obtain those credentials and connect directly to the database.  Often this results in significantly higher privileges than the client application would normally allow.
# Sniffing
The first step to investigating network communication would be sniffing what the application does on the network.
Things to watch for:
* Application Update
* [Authentication](/thick-client-authentication)
* Data manipulation
* Caching
* Plaintext vs [Encryption](/encryption)

[Sniffing Tools](/tools#sniffing)
# Interception / Modification
The idea of this section is to catch the traffic in transit and view or modify it.
[MITM Tools](/tools#mitm)
# Custom Client
As mentioned above often the goal is to access data sources directly.  In some cases this can involve creating a piece of software that mimics the client without implementing the same security controls.  Often this will start with replaying packets observed during a sniffing session.  As the protocol is better understood, more an more pieces can be altered by the custom client.  At this point various levels of [fuzzing](/fuzzing) can be attempted.

Normally custom clients have a specific target behavior or function in mind.  It is rare that we want to implement a full fledged client.  Normally we only go to the point that we can issue database queries, or send key packets that trigger server side shell commands.  Note that in an ideal testing environment we would have access to debuggers as well as reverse engineered code to guide the creation of a custom client.  We would have a goal in mind, and could use the debugger to ensure that we are following the right code paths to the target instruction.