# ChangeIP_dDNS_Update
Check external (public) IP and route to ChangeIP.com dDNS when it changes.

Running as cron job via `sudo crontab -e` so that is has root permissions.
My cron job looks like this...

```bash
SHELL=/bin/bash
HOME=/
MAILTO="email+cron_job@gmail.com"
*/15 * * * * home/username/.changeip-ddns-update/changeip-ddns-update.sh > dev/null
@reboot home/username/.changeip-ddns-update/changeip-ddns-update.sh
```

1. sets the shell
2. set the start directory
3. setup mail
4. run the bash script every 15mins, and only email me if there is an error
5. run bash script on reboot

Installation
------------

``` bash
# create directory
mkdir ~/.changeip-ddns-update
# clone git repo into new directory
git clone git://github.com/kovrinic/ChangeIP_dDNS_Update.git ~/.changeip-ddns-update
# setup cron job
sudo crontab -e
# look ^^^ to see crontab settings
```

Make sure to replace "username and email" with your credentials. Also in the changeip-ddns-update.sh change the "UserName and Password" to your changeip.com info.

Note:
-------

* Don't store passwords on GitHub, copy the script to a directory out of the git repo and enter in your private info, or follow the directions to place your password in another location and then reference them in the script.
* Change the crontab to the appropriate directory to run your personalized script.
* This script doesn't specify which dDNS, and has some security issues which are explained in the write up in the changeip-ddns-update.sh script. I'm planning on looking into how to specify which dDNS, but haven't taken time yet.
