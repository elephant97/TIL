# 도커 설치 방법
> Linux centOS 7.8

1. 시스템 패키지 업데이트
   ```
     sudo yum update
   ```
2. 필요한 의존성 설치
   ```
     sudo yum install -y yum-utils device-mapper-persistent-data lvm2
   ```
3. Docker 저장소 추가
   ```
     sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
   ```
4. Docker 설치
   ```
     sudo yum install docker-ce docker-ce-cli containerd.io
   ```
5. Docker 서비스 시작 및 활성화
   ```
     sudo systemctl start docker
     sudo systemctl enable docker
   ```
6. 설치 확인 : 테스트 컨테이너를 실행하여 확인
   ```
      sudo docker run hello-world
   ```
