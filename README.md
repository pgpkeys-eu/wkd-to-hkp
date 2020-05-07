# wkd-to-hkp

A tool to send modified keys from a Web Key Directory to one or more hkp keyservers

## Usage

This tool must be installed on the server that hosts your Web Key Directory.
It requires a POSIX system, and the utilities `gpg` and `find`.

### Quick start

Copy the sample config file into `/etc/wkd-to-hkp.conf` and edit to taste, then
copy or soft link the script `wkd-to-hkp` into `/etc/cron.hourly`.

### Security

For extra safety, you should run this command as a non-root user. You will
have to change the permissions on `SPOOLDIR` (default: `/var/spool/wkd-to-hkp`)
and invoke the command from the user's crontab (using `crontab -e`).

### Caveats

To avoid flooding the keyservers, this tool will only submit keys that have
been added or modified since it was first run. If you know what you are doing
and really want it to submit historical keys, you can `touch` some or all of
your key files so that they will be recognised as new.
