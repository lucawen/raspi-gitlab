# Raspi Gitlab
![License](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)
[![Live Demo](https://img.shields.io/badge/demo-online-green.svg?style=flat-square)](http://sv2.wakecloud.net)

This is a image for Raspberry Pi 2 witch Gitlab installed and full working.

On this image, we installed

  - NGiNX 1.9.9 (Source)
  - PHP-FPM (Native)
  - Gitlab (Mainline)

Support for HTTP2.
 
 *Example working witch ssl and using my [CloudFlare Sync] script.

### Starting
Download the image and write in your sd card.
Afte this, you need configure your rasp for run correctly.

Download in:
* [Mega]

MD5: 1626D93D88B8131EC4080DA1C276C843

SHA-1: 74321E0C30B7E0027A56E5E518D3456429509FA8

### Configure

We need to configure the hostname in system and gitlab config before anything, and configure nginx domain/subdomain if you have.

Edit hostname to your domain/subdomain or local FQN:
```sh
$ sudo nano /etc/hostname
sv2.wakecloud.net
```

Edit the gitlab config and change this to your domain/subdomain or local FQN:
```sh
$ sudo nano /etc/gitlab/gitlab.rb
[...]
external_url 'http://sv2.wakecloud.net'
[,,,]
```

Continuing in this file, look for one of these lines and edit as needed.:
```sh
gitlab_rails['smtp_enable'] = true
gitlab_rails['smtp_address'] = "smtp.mailgun.org"
gitlab_rails['smtp_port'] = 587
gitlab_rails['smtp_user_name'] = "postmaster@wakecloud.net"
gitlab_rails['smtp_password'] = "5dfb8f14a2b90bd02c70c50cae83bb22"
gitlab_rails['smtp_domain'] = "wakecloud.net"
gitlab_rails['smtp_authentication'] = "plain"
gitlab_rails['smtp_enable_starttls_auto'] = true
```
*You NEED edit this! For more infos or others smtp services, see [Gitlab SMTP Settings]

Edit the server_name in nginx block configuration to your domain/subdomain :
```sh
$ sudo nano /etc/nginx/sites-avaiable/gitlab
[...]
server_name sv2.wakecloud.net;
[...]
```
Now, you need reconfigure the gitlab configs:
```sh
sudo gitlab-ctl reconfigure
```

### Credentials and Commands

Gitlab - Username: root | Password: 5iveL!fe

Username: pi | Password: raspberry

NGiNX Commands:
```sh
sudo service nginx start|stop|restart
```
Gitlab Commands:
```sh
sudo gitlab-ctl start|stop|restart|reconfigure 
```

*And others commands...

License
----

MIT


**Free Software, Hell Yeah!**


   [CloudFlare Sync]: <https://github.com/lucawen/flaresync>
   [Mega]: <https://github.com/lucawen/flaresync>
   [Gitlab SMTP Settings]: <https://gitlab.com/gitlab-org/omnibus-gitlab/blob/master/doc/settings/smtp.md>


