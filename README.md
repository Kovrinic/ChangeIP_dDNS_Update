# ChangeIp_DDNS_Update
check external IP and route to ChangIp DDNS when it changes

Running as cron job via `sudo crontab -e` so that is has root permissions.
My cron job looks like this for now...

```bash
SHELL=/bin/bash
HOME=/
MAILTO="username+cron_job@gmail.com"
*/15 * * * * home/username/.ddns-changeip-update/changeip-ddns-update.sh > dev/null
@reboot home/username/.ddns-changeip-update/change-ddns-update.sh
```

1. sets the shell
2. set the start directory
3. setup mail
4. run the bash script every 15mins, and only email me if there is an error
5. run bash script on reboot