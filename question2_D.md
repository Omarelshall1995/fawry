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
