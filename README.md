![logo](images/MD-Cloud-logo-black.svg)<!-- .element height="10%" width="10%" -->

mdcloud cli
------------
Command line tool for metadefender cloud ip scanner designed for scanning amazon security groups.

## Build and install

The simple way of installing the tool:
```
sudo wget -q https://github.com/OPSWAT/mdcloud-go/releases/download/1.1.0/mdcloud-go_linux_amd64 -O /usr/local/bin/mdcloud && sudo chmod +x /usr/local/bin/mdcloud
```

Visit [this page](https://github.com/OPSWAT/mdcloud-go/releases) for a list of alternative downloads.

For building we use a docker image with all the dependencies installed. The image is built from `image.dockerfile` file

The docker image is hosted on a public repo on docker hub and can be downloaded locally.

Just in case, here is how to build the docker image:

```
make image VERSION=<new_version_of_docker_image>
```

For compiling the source code run:

```
make build VERSION=<version of executable>
```

This will produce a folder `dist` which contains all executables.

## Usage

Before running the tool, please make sure you have
- a metadefender cloud apikey. If not, please go to [metadefender.com](https://www.metadefender.com) and click the "Sign up" button.
- an amazon account configured (config file used by the tool is `~/.aws/credentials`)

After obtaining an apikey, you need to specify it in the command line by setting the `MDCLOUD_APIKEY` environment variable, or by passing it as an argument to the tool with `--apikey` like so:

```
mdcloud --apikey <command>
```

The outputs of the source code are executables compiled for specific platforms.

To see possible options run:
```
$ mdcloud
Metadefender Cloud API wrapper

Usage:
  mdcloud [command]

Available Commands:
  appinfo       Appinfo for hash
  cve           CVE lookup
  cves          Available CVE list
  feed          Feed of hashes, infected or false-positives
  help          Help about any command
  lookup        Lookup or download file or IP
  rescan        Rescan file
  sanitized     Sanitized result by file_id
  scan          Scan file or path
  sglist        List security groups IPs
  sgscan        Scan security groups using IP Scan API
  version       Print the version number of mdcloud-go
  vulnerability Vulnerability for hash

Flags:
  -a, --apikey string   apikey token (default is MDCLOUD_APIKEY env variable)
  -h, --help            help for mdcloud

Use "mdcloud [command] --help" for more information about a command.
```

This command relies on the fact that amazon credentials are already configured in `~/.aws/credentials`.

Licensed under the [MIT License](https://opensource.org/licenses/MIT)
