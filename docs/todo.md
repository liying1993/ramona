TODO list
=========

Generic
-------
- add version check to console-server communication handshake (and print warning if not matching)
- exitcodes option for autorestart (autorestart=1,2,3)
- (low prio): SSL (optional) for protecting console-server channel
- ulimit/resources (similar to core dump) -> minfds, minprocs
- Unify & document sys.exit codes 
- Reload/reset command (restarting ramona server)
- Restart in yield mode should also terminate & start ramona server
- [tool:x] support (how to do this properly - config is read __after__ arguments are parsed)
- console command enable/disable to allow change status during runtime
- [program:x] disabled 'magic' options:
	 - e.g. <on-platform linux:mac>
- test Ramona how it runs in out-of-diskspace conditions
- 'user' option - If ramona runs as root, this UNIX user account will be used as the account which runs the program. If ramona is not running as root, this option has no effect.
- configuration platform selector should support OR operator (e.g. pidfile@linux|darwin)
- configuration platform selector should support families (e.g. pidfile@posix); posix is so far only identified family (expanded to linux|darwin|cygwin)
- `tail -f *` to show log of **ALL** running programs
- Add support for [var] section - similar to [env] but in this case, values are not propagated into environment variables
	Otherwise it remains complementary (useful for ${VAR} expressions on command-line).
	Maybe this can be archived in a different (more elegant) way (e.g. not introduce [var]/[env] duality).
- Better error message when directory of socket file does not exist: 
    Current message when server starts: 2013-01-04 01:09:17,846 CRITICAL: It looks like that server is already running: [Errno 2] No such file or directory
- Explore eventuality of forking TTY when launching program: http://stackoverflow.com/questions/1922254/python-when-to-use-pty-fork-versus-os-fork

Logging
-------
- Support for SIGHUP (reopen log files OR reset fully)
- log rotate of Ramona server log (stdout/stderr redirection)

Configuration
-------------
- (environment) variables expansion in configuration

Watchdog
--------
- watchdog functionality (child process is signaling that is alive periodically)
- watchdog for non-managed programs (e.g. [watchdog:apache]) + restart commands

Python specific
---------------
- native python program execution (using utils.get_python_exec - substitute for STRIGAPYTHON)
- python version (minimal) check

Mailing to admin
----------------
- On autorestart mail trigger
- On FATAL mail trigger
- Mailing issues to admin: https://github.com/ateska/ramona/issues/1
- Standalone log scanner (not connected to particular program) to enable supervising of e.g. CGI scripts
- daily/weekly/monthly targets

HTTP frontend
-------------
- Store static files in a way that py2exe will work correctly.
- RESTful API
- (low prio): HTTPS

Cron
----
- Ramona can be used to trigger tasks (tools) by given time - emulating functionality of cron

Cluster
-------
- Ramona can be used as cluster controller - running on every node and managing application there.
- Ramona cluster controller needs to be built to allow single point of control
- Fail-over scenarion support
- Amazon ECS integration (e.g. use of Amazon variables that are passed to the box)
