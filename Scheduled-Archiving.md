## Schedule importing new links into your archive

To schedule regular archiving you can use any task scheduler like `cron`, `at`, `sytsemd`, etc.

ArchiveBox ignores links that are imported multiple times (keeping the earliest version that it's seen).
This means you can add cron jobs that regularly poll the same file or URL for new links, adding only new
ones as necessary.

For some example configs, see the `etc/cron.d` and `etc/supervisord` folders.

## Example: Import Firefox browser history every 24 hours

This example exports your browser history and archives it once a day:

**Create `/opt/ArchiveBox/bin/custom.sh`:**
```bash
#!/bin/bash

cd /opt/ArchiveBox
./bin/archivebox-export-browser-history --firefox ./output/sources/firefox_history.json
./bin/archivebox ./output/sources/firefox_history.json  >> /var/log/ArchiveBox.log
```

**Then create a new file `/etc/cron.d/Archivebox` to tell cron to run your script every 24 hours:**
```bash
0 24 * * * www-data /opt/ArchiveBox/bin/custom.sh
```