# Install

ArchiveBox is primarily distributed as a Python package via `pip`, but it also depends on some system packages that can be installed manually or automatically with Docker. It usually takes less than ~10min to get ArchiveBox set up and running.

<img src="https://github.com/ArchiveBox/ArchiveBox/assets/511499/601d587d-b59f-47b9-938e-8a7fa7790176" width="20%" align="right"/>



 - *[Supported Systems](#supported-systems)*
 - Install Instructions
   - **[Option A. Docker / Docker Compose ⭐️](#option-a-docker--docker-compose-setup-%EF%B8%8F)**
   - [Option B. Automatic Setup Script](#option-b-automatic-setup-script)
   - [Option C. System Package Manager Setup](#option-c-bare-metal-setup)
     - *[Upgrading ArchiveBox to a new version](#upgrading-archivebox-to-a-new-version)*
 - *[Next Steps](#next-steps)*


## Supported Systems

<img src="https://cdn0.iconfinder.com/data/icons/flat-round-system/512/freebsd-512.png" width="5%" align="right"/>
<img src="https://assets.ubuntu.com/v1/c5cb0f8e-picto-ubuntu.svg" width="5%" align="right"/>
<img src="https://imgur.zervice.io/Ue9BI7n.png" width="5%" align="right"/>

**CPU Architectures:** `amd64` (`x86_64`), `arm64` (`aarch64`), `arm7`  
*(Including 64-bit Intel/AMD, M1/M2/etc. Macs, Rasberry Pi >= 3)*

* [**macOS:**](#macos) >=10.12 (with `brew`)
* [**Linux:**](#ubuntudebian) Ubuntu (>= 18.04), Debian (>= 10), etc. (with `apt`)
* [**BSD:**](#bsd) FreeBSD, OpenBSD, NetBSD etc (with `pkg`)

Other systems are not officially supported but may work with degraded functionality:

<img src="https://imgur.zervice.io/WYSb96z.png" width="6%" align="right"/>
<img src="http://files.softicons.com/download/system-icons/web0.2ama-icons-by-chrfb/png/256x256/Operating%20System%20-%20Windows.png" width="5%" align="right"/>

 * **Windows:** Via [[Docker]], Docker in WSL2, or WSL2 without Docker (not recommended)
 * [Other UNIX systems:](https://github.com/ArchiveBox/ArchiveBox#-package-manager-setup) Arch, Nix, Guix, Fedora, SUSE, Arch, CentOS, etc.

<sub>Note: On `arm7` the `playwright` package is not available, so `chromium` must be installed manually if needed.</sub>

<br/>

You will also need at least 500MB of RAM (bare minimum), 2GB or greater is recommended. You may be able to reduce the RAM requirements if you disable all the chrome-based archiving methods with `USE_CHROME=False`.

It's also recommended to use a filesystem with compression and/or [deduplication](https://www.ixsystems.com/blog/ixsystems-and-klara-systems-celebrate-valentines-day-with-a-heartfelt-donation-of-fast-dedupe-to-openzfs-and-truenas/) (e.g. [ZFS](https://openzfs.github.io/openzfs-docs/Getting%20Started/index.html) or BTRFS) for maximum efficiency.

<br/>

---

<br/>

## Option A. Docker / Docker Compose Setup ⭐️

*Docker Compose is the recommended way to get ArchiveBox, as it includes all the extras out-of-the-box and provides the best security and upgrade UX.*

1. If you don't already have docker installed, follow the official instructions to get Docker on Linux, macOS, or Windows:  
  https://docs.docker.com/install/#supported-platforms ➡️

2. Then follow the [Quickstart](https://github.com/ArchiveBox/ArchiveBox#quickstart) guide and read the [[Docker]] wiki page for next steps. ➡️

> You can also run Dockerized ArchiveBox using [UNRAID/TrueNAS/Proxmox/etc.](https://github.com/ArchiveBox/ArchiveBox#-other-options) or [Kubernetes](https://github.com/ArchiveBox/docker-archivebox/blob/master/archivebox.yml). 

**More info:**
- [`Dockerfile`](https://github.com/ArchiveBox/ArchiveBox/blob/dev/Dockerfile)
- [`docker-compose.yml`](https://github.com/ArchiveBox/ArchiveBox/blob/dev/docker-compose.yml)
- [`archivebox-kubernetes.yml`](https://github.com/ArchiveBox/docker-archivebox/blob/master/archivebox.yml)
- [ArchiveBox Docker Quickstart](https://github.com/ArchiveBox/ArchiveBox#quickstart) + [Usage](https://github.com/ArchiveBox/ArchiveBox/wiki/Docker) + [Configuration](https://github.com/ArchiveBox/ArchiveBox/wiki/Docker#configuration) + [Upgrading](https://github.com/ArchiveBox/ArchiveBox/wiki/Upgrading-or-Merging-Archives) documentation

<br/>

---

<br/>


## Option B. Automatic Setup Script

If you're on Linux with `apt`, FreeBSD with `pkg`, or macOS with `brew` there is an optional auto-setup script provided.

*(or scroll further down for manual install instructions)*

```bash
curl -fsSL 'https://get.archivebox.io' | bash
# shortcut to run https://raw.githubusercontent.com/ArchiveBox/ArchiveBox/stable/bin/setup.sh
``` 
The script explains what it installs beforehand, and will prompt for user confirmation before making any changes to your system. The script uses Docker if already installed, but you can decline and it will attempt to auto-install everything using `apt`/`brew`/`pkg` + `pip` instead.

<img src="https://imgur.zervice.io/VMTzm0G.png" width="99%"/>

After running the setup script, continue with the [Quickstart](https://github.com/ArchiveBox/ArchiveBox#%EF%B8%8F-next-steps) guide... ➡️

> *See here for our thoughts on the [inherent limitations of `curl | sh`](https://docs.monadical.com/s/against-curl-sh) as an install method...*

<br/>

---

<br/>

## Option C. Bare Metal Setup

If you'd rather not use [Docker](https://github.com/ArchiveBox/ArchiveBox#%EF%B8%8F-easy-setup) or our [auto-install script](https://github.com/ArchiveBox/ArchiveBox#%EF%B8%8F-easy-setup), you can follow these manual setup instructions to install ArchiveBox and its dependencies using `pip` & your system package manager of choice (e.g. `apt`, `brew`, `pkg`, `nix`, etc.).

See our [Dependencies](https://github.com/ArchiveBox/ArchiveBox#dependencies) documentation to see the full list of dependencies and how they're used. Not all the dependencies are required for all modes. If you disable some archive methods you can skip installing those dependencies, for example, if you set `FETCH_MEDIA=False` you don't need to install `yt-dlp`, and if you set `FETCH_[PDF,SCREENSHOT,DOM]=False` you don't need `chromium`.

<img src="https://avatars0.githubusercontent.com/u/1503512?s=200&v=4" width="100px" align="right"/>

**More info:**
 - For help installing these, see the [Manual Setup](#manual-setup), [[Troubleshooting]] and [[Chromium Install]] pages.
 - To use specific binaries for dependencies, see the [Configuration: Dependencies](Configuration#dependency-options) page.
 - To disable unwanted dependencies, see the [Configuration: Archive Method Toggles](Configuration#archive-method-toggles) page.  



<br/>

### 1. Install base system dependencies needed for your OS

*Be aware, you'll need to keep all these packages up-to-date yourself over time!*

<img src="https://imgur.zervice.io/Ue9BI7n.png" width="30px" align="right"/>

#### macOS

Make sure you have [Homebrew](https://brew.sh/) installed first.

```bash
# Install ArchiveBox's dependencies manually (instead of using the all-in-one brew package)
brew install python3 node git wget curl ffmpeg yt-dlp ripgrep sonic
pip install archivebox
archivebox install

# Optional: get FFMPEG with the AAC addon
# brew tap homebrew-ffmpeg/ffmpeg
# brew uninstall ffmpeg; brew install homebrew-ffmpeg/ffmpeg/ffmpeg --with-fdk-aac

# Optional: get Chromium with brew (not needed if you already have /Applications/{Google Chrome,Chromium}.app)
# brew install --cask chromium
```

<img src="https://assets.ubuntu.com/v1/c5cb0f8e-picto-ubuntu.svg" width="30px" align="right"/>

#### Ubuntu/Debian-based Systems

Make sure `apt` and `dpkg` are available on your system.

```bash
# add the nodejs sources to your apt lists (optional, otherwise may use older node)
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -

# Install base system dependencies manually (check ArchiveBox/Dockerfile for more if needed)
sudo apt install python3 python3-pip python3-minimal nodejs libatomic1 zlib1g-dev libssl-dev libldap2-dev libsasl2-dev python3-ldap python3-msgpack python3-mutagen python3-regex python3-pycryptodome procps dnsutils wget curl git yt-dlp ffmpeg ripgrep
sudo apt install python3-setuptools  # or: python3-distutils on older systems

# Optional: get Chromium with pip (skip if you already have chromium-browser/google-chrome installed and in your $PATH)
# pip install --upgrade playwright
# playwright install --with-deps chromium
# OR: get chromium and manually with apt (not recommended, often out-of-date)
# sudo apt install chromium fontconfig fonts-ipafont-gothic fonts-wqy-zenhei fonts-thai-tlwg fonts-kacst fonts-symbola fonts-noto fonts-freefont-ttf
```

<img src="https://cdn0.iconfinder.com/data/icons/flat-round-system/512/freebsd-512.png" width="30px" align="right"/>


#### FreeBSD

```bash
sudo pkg install python git wget curl youtube_dl ripgrep py311-pip py311-sqlite3 npm ffmpeg
sudo pkg install chromium

# or for older versions:
# sudo pkg install python node wget curl git yt-dlp ffmpeg ripgrep chromium-browser
```

#### OpenBSD

```bash
sudo pkg_add python3 node wget git curl yt-dlp ffmpeg ripgrep chromium
```

#### Arch Linux / Nix / Guix / etc. Other OSs

See the [Quickstart](https://github.com/ArchiveBox/ArchiveBox#-package-manager-setup) instructions for other operating systems and release channels. ➡️

<br/>


<img src="https://github.com/ArchiveBox/ArchiveBox/assets/511499/65315723-adae-42e4-b8c6-e44b79165ae5" width="55px" align="right"/>

### 2. Install the Python dependencies using `pip`

It's recommended to `pip`-install ArchiveBox even if you already installed `archivebox` with one of our official `apt`/`brew` packages above (sometimes the `pip` version is newer). This step also ensures you have the latest `yt-dlp` and `playwright` versions.

```bash
# get the latest version of archivebox from PyPI
pip install --upgrade --ignore-installed archivebox[ldap,sonic]

# if you see errors about ldap, install the C++ build tools + ldap headers and retry (only needed on some OSs + if you want ldap)
# apt install build-essensial python3-ldap
```

<br/>

### 3. Install the JS dependencies using `archivebox setup`

Finish installing the runtime JS dependencies that live inside your collection data dir (e.g. readability, singlefile, mercury).
```bash
# create a new empty folder anywhere to hold your collection, and cd into it
mkdir -p ~/archivebox/data && cd ~/archivebox/data

# instantiate the directory as an archivebox collection dir
archivebox init

# auto-install all the runtime JS dependencies inside ./node_modules
archivebox setup
# under the hood, this does:
# - installs npm dependencies: singlefile, readability, puppeteer, etc.
# - installs pip dependencies: yt-dlp, playwright, etc.
# - checks for / installs sytem dependencies: curl, wget, etc
# if you see "permission denied" errors, run 'sudo archivebox setup'

# ✅ see a final detailed breakdown of all the installed dependencies and commands available
archivebox version
archivebox help
```

<br/>

### Troubleshooting

Make sure the `pip`-installed version of `archivebox` is available in your `$PATH`.
```bash
pip show archivebox      # show info about the pip-installed version of archivebox

echo $PATH               # show the directories your system is searching for binaries
which -a archivebox      # show all installed archivebox binaries available
which archivebox         # show which archivebox binary is being called

cd ~/archivebox/data
archivebox version       # ⭐️ show lots of useful info about installed dependencies and more
archivebox status
archivebox help
```
(ensure the version shown is the most recent available from [Releases](https://github.com/ArchiveBox/ArchiveBox/releases))  
  
Make sure to run `archivebox` **as an unprivileged user** (i.e. without `sudo` / not logged in as `root`).  
Make sure to run all commands, including `archivebox version`, `archivebox help`, etc. **inside a data directory** (or a new empty dir that will become a data dir).

If you have issues getting Chromium / Google Chrome or other dependencies working with ArchiveBox, see the [[Chromium Install]] and [[Troubleshooting]] pages for more detailed instructions.

<br/>

### Next Steps: Add some URLs to archive and try out CLI / Web UI


For guides on how to import URLs from different sources into ArchiveBox, check out [Input Formats](https://github.com/ArchiveBox/ArchiveBox#input-formats) and [Preparing URLs](https://github.com/ArchiveBox/ArchiveBox/wiki/Quickstart#2-get-your-list-of-urls-to-archive). ➡️

```bash
cd ~/archivebox/data
```
```bash
# feed in your URLs to start archiving!
archivebox add --help
archivebox add < ~/Downloads/bookmarks_export.html
```
```bash
# inspect the newly added Snapshots via the CLI
archivebox list
archivebox status
```
```bash
# OR start the webserver and view them in the Web UI
archivebox server 0.0.0.0:8000
open http://localhost:8000
```
See our [[Usage]] Wiki documentation page for more examples.

<br/>

### Next Steps: *Upgrading Archivebox to a new version*

Make sure all apt/brew/pkg/etc. dependencies from above are installed & up-to-date first.

```bash
# get the latest archivebox version from PyPI
pip install --upgrade --ignore-installed archivebox

# run init inside any data directories to migrate the index to the latest version
cd ~/archivebox/data
archivebox setup         # update runtime dependencies to latest versions
archivebox init          # update collection index & apply any migrations 
```

Check our more detailed [Upgrading](https://github.com/ArchiveBox/ArchiveBox/wiki/Upgrading-or-Merging-Archives) documentation and [Release Notes](https://github.com/ArchiveBox/ArchiveBox/releases) if you run into any problems. ➡️

<br/>

---

<br/>

### Further Reading

 - Read [[Usage]] to learn how to use the ArchiveBox CLI and HTML output
 - Read [[Configuration]] to learn about the various archive method options
 - Read [[Scheduled Archiving]] to learn how to set up automatic daily archiving
 - Read [[Publishing Your Archive]] if you want to host your archive for others to access online
 - Read [[Troubleshooting]] if you encounter any problems
