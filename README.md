## Contrast Security Protect - Quick Trial

[Contrast Protect](https://docs.contrastsecurity.com/en/protect.html) is a runtime web application security and observability tool. You can compare it to a WAF, although WAF is sitting external to the application and Protect is embedded inside the app and has a very high degree of accuracy compared to a WAF. No hardware or software deployment is needed. You simply intrument you application with the Contrast agent and it starts detecting and blocking attacks such as SQL Injection, Cross-site Scripting, Command Injection etc. 


## Let’s try out Protect with Webgoat 
Requriments: A Linux or Mac machine with Java installed. Basic understanding of Java , [Java Agent](https://www.developer.com/java/data/what-is-java-agent.html) , [WebGoat](https://github.com/WebGoat/WebGoat), Curl

1. Get the following attributes from the User Settings screen in the Contrast Portal. If you are not a customer you can use the free [Community Edition](https://www.contrastsecurity.com/contrast-community-edition) 
    - Organization ID, Authorization Header, API Key and Contrast URL

2. [Download WebGoat Server jar](https://github.com/WebGoat/WebGoat/releases/download/v8.1.0/webgoat-server-8.1.0.jar). Webgoat is a vulnerable application, so be careful about where you run it. Open a terminal and run steps 3 and 4 from the same folder where you placed the WebGoat jar

3. Download contrast agent jar. Replace the variables in <> with the values gathered in step 1.
    - `curl --max-time 20 https://<CONTRAST_URL>/api/ng/<ORG_ID>/agents/default/JAVA -H API-Key:<API_Key> -H Authorization:<Authorization_Header>= -o contrast.jar`

4. Start Webgoat and instrument it with the Contrast agent
    - `java -javaagent:contrast.jar -Dcontrast.standalone.appname=MyWebGoatTest  -Dcontrast.server=MyWebGoatTestServer -Dconstrast.protect.enabled=true -jar webgoat-server-8.1.0.jar`

5. Exercise WebGoat by logging into http://localhost:8080/WebGoat/, trying some attacks manually, using a DAST tool or by using [my quick and dirty curl](webgoat-curl.md)

6. Log into Contrast portal UI. You should see your server under the Servers and attack traffic under the Attacks. Pat yourself on the back and continue exploring.

