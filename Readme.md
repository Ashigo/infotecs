# Compile openssl v1.1.1_stable
Task list
- [x] Debian:9 using gcc
  - [x] Dockerfile
  - [x] compiled
  - [x] output log
- [x] Dockerfile for Debian:9 using clang-14
  - [x] Dockerfile
  - [x] compiled
  - [x] output log
- [x] Dockerfile for Windows 10 x64 using clang-14
  - [x] Dockerfile
  - [ ] compiled
  - [ ] output log

## Debian Version
Docker image build from debian:9

Created 2 versions:

- gcc variant
- clang-14 variant

### Debian gcc Version
go to path: infotex/debian/gcc_variant
```
docker build . -t debian-infotecs-gcc
docker run --name debian-infotecs-gcc debian-infotecs-gcc
docker cp debian-infotecs-gcc:/output.txt ./output.txt
```
### Debian clang-14 Version
go to path: infotex/debian/clang14_variant
```
docker build . -t debian-infotecs-clang
docker run --name debian-infotecs-clang debian-infotecs-clang
docker cp debian-infotecs-clang:/output.txt ./output.txt
```

## Windows Version
go to path: infotex/windows/clang14_variant

```
docker build . -t win-infotecs-clang
docker run --name win-infotecs-clang win-infotecs-clang
# docker cp win-infotecs-clang:/output.txt ./output.txt
```


