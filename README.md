# baba-ossdav-bin
WebDAV gateway for Alibaba Cloud OSS

OSSDav provides WebDAV interface to mount from your laptop or server

*Before you start*
1. Install Docker, OSSDav runs on Docker container
2. Get a valid pair of key and secret from your Alibaba Cloud account
3. Create a bucket

*How to install*
Download and import the image (ossdav.tar.gz) from the url
$ docker import https://github.com/nudbeach/baba-ossdav-bin/blob/master/ossdav.tar.gz

*How to run* 
From your CentOS instance,
$ docker run -it -d -p [your port]:8080 \
  -v /var:/temp -v /var/log:/logs \
  --env OSS_KEYID=[your key id] \
  --env OSS_KEYSECRET=[your key secret] \
  --env OSS_ENDPOINT=[OSS endpoint eg) oss-ap-northeast-1.aliyuncs.com] \
  --env OSS_BUCKET=[your bucket name] \
  ossdav:eg
 
*How to use*
From your windows laptop
$ net use X: http://[your instance ip]:[your port]

From the command line on your linux server
$ mount.davfs http://[your instance ip]:[your port] /mount/point

From fastab on your linux server
http://[your instance ip]:[your port]  /mnt/webdav davfs uid=username,file_mode=0664,dir_mode=2775 0 0

For further details, https://wiki.archlinux.org/index.php/Davfs

From your OS X laptop
https://support.apple.com/kb/ph18514?locale=en_US

*Note*
For large file uploads, bigger than 10MB, it runs as lazy mode. Check fragmentation tab from OSS console for the upload status 