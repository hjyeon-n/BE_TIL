# Docker 🐳

Go언어로 작성된 리눅스 **컨테이너 기반**으로하는 **오픈소스 가상화 플랫폼**이다.

### **가상화를 사용하는 이유는?** 🤷‍♀️

서버 관리자 입장에서 CPU사용률이 10%대 밖에 되지 않는 활용도가 낮은 서버들은 리소스 낭비일 수밖에 없다. 그렇다고 모든 서비스를 한 서버안에 올린다면 안정성에 문제가 생길 수도 있다. 그래서 안정성을 높이며, 리소스도 최대한 활용할 수 있는 방법으로 나타난 게 서버 가상화이다. 대표적인 가상화 플랫폼으로는 VM이 있다. 

<br>

### 컨테이너란? 📦

![image](https://user-images.githubusercontent.com/62419307/92597191-01814080-f2e2-11ea-9630-021aaf0893bb.png)

컨테이너는 가상화 기술 중 하나로 대표적으로 LXC(Linux Container)가 있다. 기존 OS를 가상화 시키던 것과 달리 컨테이너는 **OS레벨의 가상화로 프로세스를 격리시켜 동작하는 방식**으로 이루어진다.

<br>

### VM 가상화 플랫폼 vs Docker 가상화 플랫폼 ✅

![image](https://user-images.githubusercontent.com/62419307/90748332-03706900-e30d-11ea-9bba-ea56b57a9a39.png)

VM같은 경우엔 Host OS 위에 가상화를 시키기 위한 Hypervisor 엔진 그리고 그 위에 Guest OS를 올려 사용한다. 이는 가상화된 하드웨어 위에 OS가 올라가는 형태로, Host OS와 완전히 분리되는 장점은 있지만 OS위에 OS를 올리기 때문에 무겁고 느릴 수밖에 없다.

반면에 컨테이너 기반 가상화는 Docker 엔진 위에 Application 실행에 필요한 바이너리만 올라가게 된다.  컨테이너 기반 가상화는 Host OS 그리고 Docker 엔진 위에서 바로 동작하며 Host의 커널을 공유한다. 커널을 공유하게 되면 io처리가 쉽게 되어 성능의 효율을 높일 수 있다. 즉, 컨테이너를 사용하는 것은 가상 머신을 생성하는 것이 아니라 Host OS가 사용하는 자원을 분리하여 여러 환경을 만들 수 있도록 하는 것이다. 

<br>

### Docker Image 🐋

Docker Image란 컨테이너를 실행할 수 있는 실행파일, 설정 값들을 가지고 있는 것이라고 생각하면 된다. 그림과 같이 Image를 컨테이너에 담고 실행을 시킨다면 해당 프로세스가 동작하게 된다.

![image](https://user-images.githubusercontent.com/62419307/90750043-37e52480-e30f-11ea-9355-0dd6de8efa0f.png)

<br>

![image](https://user-images.githubusercontent.com/62419307/90750395-b3df6c80-e30f-11ea-9204-02a916674c9a.png)

ubuntu 이미지를 만들기 위해 Layer A,B,C가 들어간다. nginx 이미지를 만들 때는 이미 Layer A, B, C로 만들어진 ubuntu 이미지를 베이스 이미지로 사용하여 베이스 이미지에 nginx만 더하게 된다. 그렇다면 실질적으로 Layer A, B, C, nginx 가 더해진 것이지만 과정은 unbuntu + nginx가 더해진 것이다. 

web app 이미지를 만들려고 할 땐 ubuntu 이미지에 nginx를 올리고 web app을 올리는 것이 아닌 이미 만들어진 nginx 베이스 이미지에 web app을 올려 이미지를 만들게 된다.

<br>

### Docker File 🐬

Docker Image들을 저장하고 배포하는 Docker Hub는 정말 잘 활성화 되어 있다. 이미 여러 회사들은 소프트웨어를 Docker Hub를 통해 배포하기 시작했고, 우린 Docker hub에서 image를 pull하여 간단하게 컨테이너에 넣어 사용할 수 있다. 하지만 만약 배포판이 없다면? 배포판 보다 더욱 보완하고 싶다면? 그럴 때 사용 할 수 있는 것이 Docker Fille이다.

Docker File은 이미지 생성 출발점으로 이미지를 구성하기 위한 명령어들을 작성하여 이미지를 구성할 수 있다. 그 뜻은 Docker File을 읽을 수만 있다면 해당 이미지가 어떻게 구성되어 있는지도 알 수 있다는 의미가 된다.

![image](https://user-images.githubusercontent.com/62419307/90750702-281a1000-e310-11ea-848e-efb3ab570ee7.png)

<br>

### Docker Hub & Docker Registry 🐙

Docker Hub에서는 이미지를 저장하고 관리해준다. Docker Hub를 이용하면 손쉽게 image를 pull 받아 컨테이너에 적용 시킬 수 있다. (사실 GitHub와 동일하게 생각해도 무관함)

Docker Registry는 Docker Hub처럼 공개된 방식이 아닌 비공개적으로 격리된 저장소를 구축할 수 있다. 

![image](https://user-images.githubusercontent.com/62419307/90750998-86df8980-e310-11ea-86c1-6405f4108712.png)

위 그림은 Docker Image를 Pull받기 위한 url이다. 그림과 같이 앞에 있는 url을 적지 않으면 default로 Docker Hub에서 Image를 pull 받게되고, url을 적어준다면 사설 저장소에서 이미지를 받을 수 있다.

<br>

### Docker Architecture 🐠

![image](https://user-images.githubusercontent.com/62419307/90751335-f6ee0f80-e310-11ea-87a6-d3d692d82732.png)