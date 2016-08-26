Sheepdog
========

<img src="http://contrast-security-oss.github.io/meow/images/sheepdog-cat.png" alt="Image of SheepDogCat" width="200"/>

Sheepdog is a simple tool to generate normal and attack traffic for OWASP WebGoat. It can be used with security technologies like WAF and RASP in demonstrations and to verify that they are doing a tiny piece of what they are supposed to do. Sheepdog is not intended to be an exhaustive set of security tests. It has some basic SQL injection, XSS, path traversal, and that kind of thing.

Simply start WebGoat with:

> java -jar webgoat-container-7.0.1-war-exec.jar

Then in another window start sheepdog with:

> java -jar sheepdog-1.0.jar

There are several configurable properties that you can use to simulate a variety of crawls/attacks.

> Usage: java -jar sheepdog.jar #threads #durationMins #ratePerMin #attackPercent port


# Features:
* Configurable number of attack threads
* Configurable overall duration
* Configurable request rate per attack thread
* Configurable percentage of requests which contain attacks
* Configurable port for WebGoat
* Uses X-Forwarded-For header with random IP address for each attack thread


## Sample usage

	$ java -jar sheepdog-1.0-SNAPSHOT.jar 3 120 5 80
	Usage: java -jar sheepdog.jar #threads #durationMins #ratePerMin #attackPercent port
	Starting 3 attack threads, each with:
	  120 minute duration
	  5 requests per minute
	  80% attack parameters
	  target: http://localhost:8080/WebGoat/
	
	  Starting AttackThread (238.20.254.102)
	  Starting AttackThread (93.65.24.224)
	  Starting AttackThread (161.144.64.146)
	
	POST from 238.20.254.102 to http://localhost:8080/WebGoat/j_spring_security_check
	   [username=guest, password=guest]
	   HTTP/1.1 302 Found
	
	POST from 93.65.24.224 to http://localhost:8080/WebGoat/j_spring_security_check
	   [username=guest, password=guest]
	   HTTP/1.1 302 Found
	
	POST from 161.144.64.146 to http://localhost:8080/WebGoat/j_spring_security_check
	   [username=guest, password=guest]
	   HTTP/1.1 302 Found
	
	POST from 161.144.64.146 to http://localhost:8080/WebGoat/attack?Screen=733&menu=1200
	   [SUBMIT=zoees822]
	   HTTP/1.1 200 OK
	
	POST from 93.65.24.224 to http://localhost:8080/WebGoat/attack?Screen=534&menu=1900
	   [id=sztol903, SUBMIT=rjeee272]
	   HTTP/1.1 200 OK
	
	POST from 161.144.64.146 to http://localhost:8080/WebGoat/attack?Screen=726&menu=200&stage=1
	   [action=' or 112=112--]
	   HTTP/1.1 200 OK
	
	POST from 161.144.64.146 to http://localhost:8080/WebGoat/attack?Screen=737&menu=1100&stage=3
	   [action=' or 1+2=3 --]
	   HTTP/1.1 200 OK
	
	POST from 93.65.24.224 to http://localhost:8080/WebGoat/attack?Screen=498&menu=1300
	   [clear_user=><script>alert(1)</script>, clear_pass=><script>alert(1)</script>, Submit=ctyna446]
	   HTTP/1.1 200 OK



## Who made this?
This project is sponsored by [Contrast Security](http://www.contrastsecurity.com/) and released under the MIT license.

![Contrast Security Logo](http://cdn2.hubspot.net/hub/203759/file-2275798868-png/theme/Contrast-logo-transparent.png "Contrast Logo")