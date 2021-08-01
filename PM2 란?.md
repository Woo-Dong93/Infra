# PM2



### 1. PM2란?

- 공식 문서 : PM2는 Node.js 어플리케이션을 쉽게 관리할 수 있게 해주는 Process Manager입니다. 
- Node.js 어플리케이션을 cluster mode 로 실행시킨다거나, 메모리가 넘친다거나, 오류로 인해 프로세스가 종료되는 등의 상황에 직면했을 때 각각의 상황을 사용자가 모두 신경 써서 처리해줄 수도 있지만, 너무 복잡하고 신경 써야 할 일들이 많아지게 됩니다.
- PM2를 이용하면 간단한 설정만으로도 이러한 처리를 손쉽게 해결할 수 있습니다.





### 2. Cluster Mode

- PM2의 cluster 모드는 Node.js의 Cluster Module을 이용해 기본적으로 싱글 스레드인 Node.js를 멀티 스레드로 구동시켜 줍니다.
- 싱글 스레드의 경우 구동 중인 서버의 CPU 개수와 상관없이 1개만 사용할 수 있기에 서버의 성능이 제대로 동작하지 않을 수 있습니다.
- 멀티 스레드는 최대 서버 CPU 수만큼 프로세스를 생성해 최대 성능을 끌어낼 수 있습니다.
  - 하이퍼스레딩을 지원한다면 2배 더 프로세스를 생성할 수 있습니다.



### 3. **Node.js - Cluster module**

- Node.js의 단일 인스턴스는 단일 스레드에서 실행되는데, 멀티코어 시스템을 이용하기 위해서 Node.js 프로세스들을 클러스터로 사용할 수 있습니다. 이를 통해 **모든 서버 port를 공유하는 하위 프로세스를 생성**합니다.

- 이 하위 프로세스들은 `child_process.fork()` 메서드를 사용해서 생성되는데, 부모 자식 간의 통신을 위한 IPC(Inter-process communication) 채널을 가지고 있으며 **생성된 각 프로세스는 자체 V8인스턴스**가 있습니다.





#### 참고 링크

- https://engineering.linecorp.com/ko/blog/pm2-nodejs/
- https://short-term.tistory.com/6