# 쿠버네티스 시작하기

## 참고

[쿠버네티스 시작하기](https://docs.docker.com/get-started/)
[유툽/백기선/도커](https://www.youtube.com/playlist?list=PLfI752FpVCS84hxOeCyI4SBPUwt4Itd0T)

## 유툽 인덱스

### 쿠버네티스 시작하기 1부. minikube와 kubectl 사용해서 앱 배포하기

[![쿠버네티스 시작하기 1부. minikube와 kubectl 사용해서 앱 배포하기](https://img.youtube.com/vi/IFc1mG48j0s/0.jpg)](https://youtu.be/IFc1mG48j0s)

쿠버네티스란 무엇인가. 쿠버네티스의 매니저와 노드에 대해 알아봤습니다. 그리고 웹에서 인터렉티브 하게 미니큐브를 사용해 간단한 애플리케이션을 배포하는 것 까지 살펴봤습니다.

https://kubernetes.io/docs/tutorials/kubernetes-basics/explore-intro/

여기서 1과 2에 해당하는 내용보고 2 마무리 하는 도중에 갑자기 스트리밍이 끊겼어요.

Deployment라는 걸 만들어서 배포하면 Pod라는게 생기고 그게 애플리케이션 단위인것 같은데 Pod에 대해서는 3부에서 더 자세히 다룬다고 합니다. 원래 3부까지 보려고 했는데 스트리밍이 갑자기 끊어지는 바람에.. 다음에 이어서 보겠습니다.

### 쿠버네티스 시작하기 2부. Pod, Node 그리고 Service

[![쿠버네티스 시작하기 2부. Pod, Node 그리고 Service](https://img.youtube.com/vi/lVG9LU90ZQw/0.jpg)](https://youtu.be/lVG9LU90ZQw)

쿠버네티스의 Pod, Node 그리고 서비스에 대해 살펴봤습니다. (3, 4번 모듈)

https://kubernetes.io/docs/tutorials/kubernetes-basics/expose-intro/

쿠버네티스의 포드? 파드? 는 컨테이너들과 그 컨테이너들끼리 공유할 수 있는 리소스들의 묶음이고 파드당 아이피가 하나 할당이 됩니다. 즉 그 안에 있는 컨테이너들끼리는 같은 IP 를 공유해서 쓰는거겠죠.

그리고 Node는 그 Pod 실행하는 실제 워커 머신인데, 하나의 노드 안에 여러개의 파드를 실행할 수도 있다고 합니다. 그리고 노드는 그 안에 컨테이너들과 큐비클이라는게 있고, 큐비클이 실제 쿠버네티스 매니저랑 의사소통 하면서 컨테이너들을 어떻게 뛰울지 상태를 바꿀지 결정합니다.

그렇게 어떤 노드 안에 돌고 있는 파드안에 들어있는 컨테이너에 접근을 하려면 지금까지는 kubectl proxy를 띄워서 접속했었는데요. 서비스라는 걸 쓰면 그렇게 private하고 isolated된 네트워크에서 돌고 있는 애플리케이션을 클러스터 밖으로 노출시킬 수 있습니다.

서비스는 여러 파드들의 묶음인데 아마도.. 레이블로 사용해서 묶는거 같고요. (이부분은 저에게 명확하지 않습니다.) 라우팅과 디스커버리도 담당합니다. 서비스에서 중요해 보이는게 타입인데, 이 타입에 따라 클러스터 밖으로 노출하는 방법이 달라집니다.

데모에서는 NODE_PORT 라는 타입을 사용해서 특정 애프리케이션이 사용하는 포트를 지정해주면, 그 포트에 접근할 수 있는 공개된 포트를 랜덤하게 만들어 주더군요. 그럼 그 포트 번호화 미니큐브가 돌고 있는 IP를 조합해서 클러스터 밖에서도 애플리케이션에 접속할 수 있게 되었습니다.

### 쿠버네티스 시작하기 3부 (완결): 애플리케이션 스케일링과 롤링 업데이트

[![쿠버네티스 시작하기 3부 (완결): 애플리케이션 스케일링과 롤링 업데이트](https://img.youtube.com/vi/6q1MRXNUzPU/0.jpg)](https://youtu.be/6q1MRXNUzPU)

오늘로 쿠버네티스 시작하기 3부가 완료됐습니다.

https://kubernetes.io/docs/tutorials/kubernetes-basics/

쿠버네티스 기본 5부과 6부가 생각보다 짧아서 금방 봤네요. 오토스켈링 기능도 제공한다고 하는데 튜토리얼에서 다루진 않았습니다. 비교적 간편하게 큐브컨트롤(kubectl)을 사용해서 스케일 아웃, 스케일 인 할 수 있었습니다.

여러 인스턴스를 띄워둔 경우에 무중단 배포도 쿠버네티스로 할 수 있는데, 롤링 업데이트라고 하더군요. 그런데 기본값으로는 모든 파드를 다 내리고 한번에 새 파드를 다 만들어서 중단이 생길 수도 있을거 같은데, 뭔가 비율을 조정할 수 있을 것 같은데 이것도 역시 튜토리얼에서 다루진 않네요.

개인적으로 도커 스왐보다 재밌고 다양한 기능을 제공하는것 같아 마음에 드네요. 다음 기회에 더 자세히 살펴보겠습니다.
