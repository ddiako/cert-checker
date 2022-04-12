# CERT-CHECKER

## Description

A script to check SSL certificate expiration date of a list of sites.

The script can be launched in two modes:

* **Terminal**: Output is displayed in your terminal
* **HTML**: the script generates an HTML file (called **certs_check.html** by default) that can be opened with your browser. 

Optionally, you can also embed the HTML and send it via:

* **email**: you will need to install **mutt** if you use this option
* **slack**: install **imgkit** via pip and **wkhtmltopdf** using your distribution package manager (in RHEL/CentOS you will need to enable EPEL first) Don't forget to configure you Slack Token the **slack_token** variable of jota-cert-checker.sh script

## Usage

For example, we have the following file called sitelist that contains a list of domains with the HTTPS port, one domain per line:

```
linux.com:443
kernel.org:443
gnu.org:443
debian.org:443
ubuntu.com:443
github.com:443
google.es:443
redhat.com:443
superuser.com:443
youtube.com:443
stackoverflow.com:443
stackexchange.com:443
wikipedia.org:443
python.org:443
codecademy.com:443
packtpub.com:443
reddit.com:443
mysql.com:443
```

In the following cases I modified the variables **warning_days** and **alert_days** for sample purposes. 

To launch the script in terminal mode:
```bash
./cert-checker.sh -f sitelist -o terminal
```
We get the following output in our terminal:

![screenshot from 2022-04-12 - console](/img/cert-checker-console.png)

In HTML mode:
```bash
./cert-checker.sh -f sitelist -o html
```
We get the following output:

![screenshot from 2022-04-12 - html](/img/cert-checker-html.png)

In HTML mode and sending the result to an email:
```bash
./cert-checker.sh -f sitelist -o html -m mail@example.com
```
Checking our email we will see:

![screenshot from 2018-02-11 20-30-11](https://user-images.githubusercontent.com/12804701/36078161-891bb566-0f73-11e8-984c-1cd65127a8e4.png)

Also in HTML mode and sending the result to a slack channel:
```bash
./cert-checker.sh -f sitelist -o html -s my_slack_channel
```
