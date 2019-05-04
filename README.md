APT / Debian Repository
=======================

Configure the repository:

```bash
curl -s https://apt.miniflux.app/KEY.gpg | sudo apt-key add -
echo "deb https://apt.miniflux.app/ /" > /etc/apt/sources.list.d/miniflux.list
apt update
apt install miniflux
```

Instructions to update the repo:

```bash
docker run -it --rm -v `pwd`:/repo debian:latest \
    bash -c "apt update && apt install -y apt-utils && cd /repo && apt-ftparchive --arch amd64 packages . > Packages && gzip -k -f Packages && apt-ftparchive release . > Release"
gpg --default-key $GPG_KEY_ID -abs -o - Release > Release.gpg
gpg --default-key $GPG_KEY_ID --clearsign -o - Release > InRelease
```

