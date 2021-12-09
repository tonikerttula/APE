# OWASP Zap Proxy

Proxy is a useful tool when probing websites, and it can for example manipulate requests and stop the directions on the website. OWASP ZAP is ready installed tool found in Kali!
To start using it open it by searching zap in your local system, and clicking the program.

#### WARNING! Using a proxy is legal, proxying is thought as passive scanning. _HOWEVER_, using the attacks available in ZAP should be used ONLY to machines and websites you own on your own systems, it's illegal to run active scans without permission!

You'll need a certificate for ZAP to fake a HTTPS connection. You can generate one by navigating in ZAP to Tools -> Options -> Dynamic SSL Certificates. From "Generate" you can generate a new certificate, and click "Save" to save it. By default it'll be saved with a name "owasp_zap_root_ca.cer".

![](https://tonikerttula.files.wordpress.com/2021/11/image-152.png)

Next, open your browser, preferably Firefox. Open Preferences, and type in the search box "certificate" to find "View Certificates" button under Privacy & Security.

![](https://tonikerttula.files.wordpress.com/2021/11/image-153.png)

Click "View Certificates" to open the following window:

![](https://tonikerttula.files.wordpress.com/2021/11/image-154.png)

Click "Import", and choose the just generated certificate.

![](https://tonikerttula.files.wordpress.com/2021/11/image-155.png?w=1024)

Set the Trust settings followingly:

![](https://i.gyazo.com/fd902402cf7dd8b6a3a356ae01825226.png)

Next you'll need to configure ZAP to use a specific port. You'll find this in the ZAP and navigating to Tools -> Options -> Local Proxies. Choose the address as __127.0.0.1__ and port as __8080__.

![](https://tonikerttula.files.wordpress.com/2021/11/image-156.png)

Now to use it in browser, add "FoxyProxy" addon in Firefox. Just search it on web, go to the Firefox addons and click "Add to Firefox". The FoxyProxy icon will appear in your browsers top right. Click it and choose Options -> Add to create a new proxy.

Name it "ZAP" and configure the following settings:

1. Proxy Type: HTTP
2. Proxy IP: 127.0.0.1
3. Port: 8080

![](https://tonikerttula.files.wordpress.com/2021/11/image-157.png?w=1024)

Now turn on your proxy from the Foxy icon in your Browser and choosing ZAP

![](https://i.gyazo.com/29468a194dd1deebe9dd64a722cc6b98.png)

Turn on your Metasploitable 2 machine, and type it's IP-address on your URL-bar. Remember to run the ZAP program on your machine, and start a new session! You should have the HUD pop up, and you can start making yourself comfortable with ZAP by completing the tutorial!

![](https://i.gyazo.com/327dc7afe753f16c45bee2f6996cb9fc.png)
