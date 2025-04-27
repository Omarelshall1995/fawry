Please Follow the Readme.MD OR YOU CAn also click on the screenshots i have provided, it will be put below, feel free

![fawry test](Fawry.png)


Question 1A:
the script first checks if the user asked for help  
then it looks at the options like -n or -v or both  
after that it expects the search word and the file name  
if it something is missing it shows an error and stops

Question 1B:
if i wanted to support more options like regex or -i or -c or -l  
i will maybe use getopts to make it easier to read
then depending on the option or counting will change

Question 1C:
the hardest part was making -v and -n work together, and the missing argument part, but i have managed to solve it thanks !
------------------------------------------

Question 2_A 
Verify DNS Resolution:
i tried to ping internal.example.com but it failed because the domain does not exist
then i used nc to check if ports 80 and 443 are open
both tests failed as expected

screenshots are attached for the command 
(Q2 A.png) 
(Q2 A - PART3.png)

Question 2_B 

i tried to ping internal.example.com but it failed because the domain does not exist
then i used nc to test if ports 80 and 443 are reachable
both tests failed which is expected since there is no real server
i also tried curl to connect to the service but it failed too
screenshots are attached
(Q2 B.png)

Question 2_C
dns server is misconfigured or unreachable
wrong dns record for internal.example.com
firewall is blocking access to port 80 or 443
web server is running but listening only on localhost
wrong ip address assigned in dns
routing issues between the user and the server
ssl certificate problem (if trying https on port 443)
server is up but the web service is down or crashed
Question 2_D ( Commands ) 
if the dns server is misconfigured or unreachable
i would check which dns server my system is using by running cat /etc/resolv.conf
if it is wrong, i would edit the file and set it to a correct dns server like 8.8.8.8

if the dns record for internal.example.com is wrong
i would run dig internal.example.com and see if the ip address is correct
if it is wrong i would update the dns record on the dns server

if the firewall is blocking port 80 or 443
i would run nc -zv server_ip 80 and nc -zv server_ip 443
if the ports are closed i would open them by allowing ports 80 and 443 in the firewall

if the web server is listening only on localhost
i would run netstat -tulnp or ss -tulnp to see where it is listening
if it is only listening on 127.0.0.1 i would fix the web server config to listen on 0.0.0.0

if the wrong ip address is assigned in dns
i would run dig +short internal.example.com and compare the ip to the real server ip
if it is wrong i would correct the dns A record

if there are routing issues
i would ping the server ip and use traceroute to see where it fails
then i would fix the route or network settings

if there is an ssl certificate problem
i would try curl -v https://internal.example.com to see the ssl error
if the certificate is expired or wrong i would renew or fix it

if the web service itself is down
i would try curl http://server_ip or check the service status
if it is down i would restart the web service like nginx or apache


