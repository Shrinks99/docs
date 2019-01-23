Make sure you have Docker installed and set up:

If you don't already have docker installed, follow the official install instructions for Linux, macOS, or Windows https://docs.docker.com/install/#supported-platforms.

# Docker Compose

An example `docker-compose.yml` config is included in the project root.  You can edit it as you see fit, or just run the default setup with archivebox + nginx as it comes out of the box:

```bash
cd /path/to/ArchiveBox
docker-compose up -d
```
Then open https://127.0.0.1:8098 to view the archive.

To add new URLs, you can use docker-compose just like the normal `./archive` CLI: 
```bash
# pass links to archive via stdin
echo "https://example.com" | docker-compose exec -T archivebox archive

# or pass the URL of a feed to import links from
docker-compose exec archivebox /bin/archive https://example.com/some/feed.rss

# or import a file by putting it in your data folder so docker can access it
mv ~/Downloads/bookmarks.html data/sources/bookmarks.html
docker-compose exec archivebox /bin/archive /data/sources/bookmarks.html
```

To pass in environment variables for configuring ArchiveBox,  
edit `docker-compose.yml` or create a `.env` file in the project root.

# Docker

1. Fetch and build the ArchiveBox Docker image:
```bash
docker build github.com/pirate/ArchiveBox -t archivebox
```

2. Create a volume to hold your ArchiveBox data:
```bash
docker volume create archivebox-data
```

2. Run ArchiveBox with `docker run` to add links to your archive:

To add a list of pages via URL of a feed.
```bash
docker run -v archivebox-data:/data archivebox 'https://example.com/some/rss/feed.xml'
```

To add a single link or a list of links from a file, pipe them in via stdin.
```bash
echo 'https://example.com' | docker run -i -v archivebox-data:/data archivebox
# or
cat bookmarks.html | docker run -i -v archivebox-data:/data archivebox
```

To pass configuration parameters, you can use the env command.
```bash
echo 'https://example.com' | docker run -i -v archivebox-data:/data archivebox env FETCH_SCREENSHOT=False /bin/archive
```

Or you can define an `ArchiveBox.env` file and pass it in like so:
```bash
docker run -i -v --env-file=ArchiveBox.env archivebox /bin/archive ...
```