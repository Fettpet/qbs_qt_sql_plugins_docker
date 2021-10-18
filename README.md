# Docker Image with Qbs, clang and Qt
This docker image is used to compile source code with qbs build system. The Qt has compiled [sql plugins](https://doc.qt.io/qt-5/sql-driver.html).

## Supported Driver
* QDB2	:x: 
* QIBASE	:x: 
* QMYSQL :heavy_check_mark: 
* MARIADB	:x: 
* QOCI	:x: 
* QODBC	:x: 
* QPSQL	PostgreSQL :heavy_check_mark: 
* QSQLITE2	:x: 
* QSQLITE	:x: 
* QTDS :x: 

## Usage

To compile the source code with the docker file you can run

```bash
docker run  \
--network="host" \ # grant access to the databas server on the host
--rm  \ # cleans up after finishing
-v /source:/build \ # mount the source to the build directory /build
-w /build \ # use /build as working directory
ghcr.io/fettpet/qbs_qt_sql_plugins_docker:qt5.15.2-qbs1.20.1-clang10 \ # path to the container.
qbs build --build-directory /tmp/build  -p autotest-runner # the qbs build 
```