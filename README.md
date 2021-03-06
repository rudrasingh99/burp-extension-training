# burp-extension-training

## Requirements
Python >=3.6 <br>
Flask <br>
Burp <br>
Jython 2.7.1 Standalone (http://search.maven.org/remotecontent?filepath=org/python/jython-standalone/2.7.1/jython-standalone-2.7.1.jar)

## To Run
```git clone https://github.com/sunnyneo/burp-extension-training.git```
### Server-Side
```
pip install flask
export FLASK_APP=webserver.py
flask run
```
### Client-Side
```java -jar -Xms2G burpsuite_pro_v1.7.36.jar```

#### Configure Burp with Jython
```
Burp -> Extender -> Options

Jython Standalone 2.7.1
```

## Challenge 1
http://127.0.0.1:5000/1/

### Objective
Develop an extension for session handling rule that have the following functions
* Automatically update the request with the custom header value obtained from http://127.0.0.1:5000/token/
* The generated token will be cleared after every 5 successful requests or 10 tokens generated. 
* Get "statusmsg: Request successfully received" for all requests sent to the server.  

```
curl -v http://127.0.0.1:5000/1/
curl -v http://127.0.0.1:5000/token/
curl -v http://127.0.0.1:5000/1/ -H 'secret-token: 070dc567-4ab8-4a62-a212-c845c6dfdae2'
```

### Template
c1_session_action.py


## Challenge 2
http://127.0.0.1:5000/2/

### Objective
Develop an extension that have the following functions
* Able decode encoded values and allow on the fly modification during 'intercept'.
* Able to perform Active Scan for parmeter with an encoded value.
* Able to generate payloads for Intruder and Intruder can process the payload further so that it can be accepted by the application.
* Get "statusmsg: Request successfully received" along with your tampered value displayed.

### Template
c2_custom_tab.py
c2_custom_scanner_insertion_point.py
c2_intruder_payload_processor.py


## Challenge 3
http://127.0.0.1:5000/3/

### Objective
Develop an extension that have the following functions
* Able decode encoded values and allow on the fly modification during 'intercept'.
* Able to perform Active Scan for parameters encapsulated in the encoded value.
* Able to generate payloads for Intruder and Intruder can process the payload further so that it can be accepted by the application.
* Get "statusmsg: Request successfully received" for all requests sent by Burp

### Template
c3_custom_tab.py
c3_custom_scanner_insertion_point.py
c3_intruder_payload_processor.py


## Challenge 4 
http://127.0.0.1:5000/4/start 

### Objective
Develop a passive scanner extension to flag out all the URLs with "secret" header in the response so that all the affected URLs can be exported from Burp to a report writing tool 

### Template
c4_passive_scanner.py


## References
All the codes here are based on the codes shared on PortSwigger Github repository. 
```
https://github.com/PortSwigger/
https://github.com/PortSwigger/example-custom-editor-tab/
https://github.com/PortSwigger/example-custom-scan-insertion-points/
https://github.com/PortSwigger/example-intruder-payloads
https://github.com/PortSwigger/ssl-scanner
```

## Other References
```
https://www.twelvesec.com/2017/05/05/authorization-token-manipulation/
https://github.com/securityMB/burp-exceptions/
https://github.com/danielmiessler/SecLists/blob/master/Fuzzing/XSS-JHADDIX.txt
```