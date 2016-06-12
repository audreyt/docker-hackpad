# istepanov/hackpad

[Hackpad](https://github.com/dropbox/hackpad) Docker image

Docker Hub [link](https://hub.docker.com/r/istepanov/hackpad/)

### Environment variables

* `ADMIN_EMAILS` - comma-separated superuser emails (default: `admin@example.com`)
* `DB_HOST` - mysql host (default: `mysql`)
* `DB_PORT` - mysql port (default: `3306`)
* `DB_NAME` - mysql database name (default: `hackpad`)
* `DB_USERNAME` - mysql user (default: `hackpad`)
* `DB_PASSWORD` - mysql user password (default: `password`)
* `TOP_DOMAINS` - comma-separated top level domains (default: `localhost,localbox.info`)

### Installing on Google Compute Engine

After `sudo docker-compose up`, enter the container with `sudo docker exec -it dockerhackpad_hackpad_1 bash`, make modifications, then restart the compose cluster.

Additional settings in `/home/hackpad/hackpad/etherpad/etc/etherpad.local.properties.tmpl` :

```
etherpad.canonicalDomain = pad.g0v.link
transportUseWildcardSubdomains = false
smtpServer = smtp.mailgun.org:2525
alwaysHttps = true
customEmailAddress = (from mailgun config)
smtpUser = (from mailgun config)
smtpPass = (from mailgun config)
```

Emoji installation:

```
cd hackpad/etherpad/src/static/img/emoji/unicode/
wget https://github.com/github/gemoji/archive/master.zip
apt-get install -y unzip
unzip master.zip
mv gemoji-master/images/emoji/unicode/* .
rm -rf gemoji-master/
```
