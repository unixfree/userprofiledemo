참고 URL :  아래 A만 우선 참고하시면 됩니다. <br>
<br>
A) 기본 사용법 설명 ( Server + Sync Gateway + Couchbase Lite ) <br>
https://docs.couchbase.com/tutorials/userprofile-sync/userprofile_sync.html <br>
B) 기본 사용법 설명 ( Couchbase Lite Only) <br>
https://docs.couchbase.com/tutorials/userprofile-standalone/userprofile_basic.html <br>
C) 소스(GitHub) <br>
https://github.com/couchbaselabs/userprofile-couchbase-mobile <br>
D) IOS 용 소스(GitHub) <br>
https://github.com/couchbase-examples/ios-swift-cblite-userprofile-sync <br>
E) ReactNative 기반 클라이언트 사용시. <br>
https://github.com/couchbaselabs/userprofile-couchbase-mobile-reactnative <br>
<br>
<br>
아래는 MacOS에 Couchbase Server 와 Sync Gateway 패키치를 설치하여 구성하는 방법이고. <br>
첨부 문서는 Docker container를 사용해서 Couchbase Server 와 Sync Gateway 를 구성하는 방법입니다. <br>
<br>
1. Couchbase Server 설치 및 구성.<br>
1-1. Install Couchbase Server at MacOS<br>
 https://www.couchbase.com/downloads 에서 "Server" > Couchbase Server(Enterprise) 다운로드  <br>
1-2. Couchbase 설치 <br>
 참고 : https://docs.couchbase.com/server/current/install/macos-install.html <br>
 MacBook의 메모리가 최소 8GB, 16GB 이상 권장. <br>
1-3. Couchbase 기본 관리 계정 (Administrator / [password] ) <br>
1-4. Bucket 생성 : userprofile <br>

1-5. Sync Gateway 접속 계정 생성 : admin / [password]  <br>
<br>


2. Sync Gateway 설치 및 구성 <br>
2-1. Install Sync Gateway<br>
2-1-1. https://www.couchbase.com/downloads 에서 "Mobile & Edge" > Sync Gateway(Enterprise) <br>
<br>
or<br>
$ wget https://packages.couchbase.com/releases/couchbase-sync-gateway/3.2.0/couchbase-sync-gateway-enterprise_3.2.0_arm64.zip?_gl=1*1das0cc*_gcl_au*MTA4ODgyNzUyMC4xNzI3MDQ4NjMx <br>
<br>
2-1-2. rpm -i couchbase-sync-gateway-enterprise_3.1.0_x86_64.rpm <br>
$ ls /opt/couchbase-sync-gateway <br>
<br>
2-2. make config.json <br>
참고 : https://github.com/couchbaselabs/userprofile-couchbase-mobile/blob/sync/content/modules/userprofile-sync/examples/sync-gateway-config-userprofile-demo-3-x-legacy.json <br>
<br>
$ vi /Users/paul/config.json <br>
 위 json에서 server connection, id/password 등 수정. <br>
<br>
2-3. Sync-gateway 구동  <br>
$ /opt/couchbase-sync-gateway/bin/sync_gateway /Users/paul/config.json <br>
<br>
4. IOS Client/SDK 구성 및 빌드 <br>
https://github.com/couchbase-examples/ios-swift-cblite-userprofile-sync <br>
<br>
$ cd /Users/paul/Documents/Workplace/Couchbase/mobile
$ gh repo clone couchbase-examples/ios-swift-cblite-userprofile-sync
$ cd ios-swift-cblite-userprofile-sync/src
$ ./install_tutorial.sh 3.2.1   -> check "Frameworks" Folder in current Directory.
<br>
<br>
open UserProfileSyncDemo.xcodeproj at Xcode.<br>
Build.<br>
