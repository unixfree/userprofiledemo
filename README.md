## 참고 URL <br>
 아래 A만 우선 참고하시면 됩니다. <br>
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
이 소스는 카우치베이스 DB, Sync Gatewat, Couchbase Lite가 어떻게 동작하는지는 보여 주는 데모입니다. <br>
아래에 설명된 내용은 MacOS에 <br>
1) Couchbase Server 설치 및 구성, <br>
2) Sync Gateway 패키치를 설치하여 구성, <br>
3) IOS용 클라이언트 앱을 구성.실행하는 방법을 설명합니다. <br>
<br>

## 1. Couchbase Server 설치 및 구성.<br>
1-1. MacOS용 카우치베이스 패키지 다운로드 및 설치 구성. <br>
- MacBook의 메모리가 최소 8GB, 16GB 이상 권장. <br>
- 아래 링크에 카우치 설치방법이 설명되어 있습니다. <br>
   https://receptive-blender-fda.notion.site/Couchbase-Install-on-MacOS-1342845c3696806387fdc02b67e2a7c9 <br>
- Couchbase 기본 관리 계정 : Administrator / password  <br>
<br>
1-2. 본 데모를 위한 Bucket 생성 : userprofile <br>
- 좌측 메뉴에서 "Bucket" 선택 > 우측 상단에서 "ADD BUCKET" 선택 <br>

![Application](AddBucket1.png)

- Name 에 "userprofile" 입력, Memory Quota에 "200"MB 입력 후 , "Add Bucket" 실행. <br>

<br>
<br>
1-3. Sync Gateway 접속 계정 생성 : admin / password  <br>

<br>


## 2. Sync Gateway 설치 및 구성 <br>
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

## 3. IOS Client/SDK 구성 및 빌드 <br>
3-1. gitbub에서 다운로드 및 구성.
<br>
$ cd /Users/paul/Documents/Workplace/Couchbase/mobile
$ git clone couchbase-examples/ios-swift-cblite-userprofile-sync
$ cd ios-swift-cblite-userprofile-sync/src
$ ./install_tutorial.sh 3.2.1   -> check "Frameworks" Folder in current Directory.
<br>
<br>
3-2. Xcode에서 Project 오픈, Build, Run <br>
open UserProfileSyncDemo.xcodeproj at Xcode. <br>

Build.<br>
