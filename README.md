SlowlorisChecker
================

This is a simple script to check if some server could be affected by Slowloris attack (Not executing the attack itself)

=======================
According to the origional author - translated to English

Since nmap's slowloris script doesn't work 

 I have decided to do the same test in an ad hoc way but it is based on the
 same mechanics:
                                                                              
 We open two connections at the same time to the server:
 1 - Control connection: This connection will not send anything other than a pair of
 headers and wait for the server to timeout.
 2 - Delay connection: This connection is created at the same time as the first one,
     send the same headers, wait 10 seconds and send one more header
     to the server. Wait for the server to timeout.
                                                                              
 If there is a time difference between timeout 1 and 2 of 10 seconds or
 more, then we can conclude that the server is vulnerable to this attack,
 since a connection can be kept busy on the server while it is
 send headers every 10 seconds (configurable time).

Full explanation of the method used taken from the following link:

https://community.qualys.com/blogs/securitylabs/2011/07/07/identifying-slow-http-attack-vulnerabilities-on-web-applications
