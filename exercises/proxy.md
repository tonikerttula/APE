# OWASP Zap Proxy

Proxy is a useful tool when probing websites, and it can for example manipulate requests and stop the directions on the website. OWASP ZAP is ready installed tool found in Kali!
To start using it open it by searching zap in your local system, and clicking the program.

You'll need a certificate for ZAP to fake a HTTPS connection. You can generate one by navigating in ZAP to Tools -> Options -> Dynamic SSL Certificates. From "Generate" you can generate a new certificate, and click "Save" to save it. By default it'll be saved with a name "owasp_zap_root_ca.cer".

![](https://tonikerttula.files.wordpress.com/2021/11/image-152.png)

Next, open your browser, preferably Firefox. Open Preferences, and type in the search box "certificate" to find "View Certificates" button under Privacy & Security.
