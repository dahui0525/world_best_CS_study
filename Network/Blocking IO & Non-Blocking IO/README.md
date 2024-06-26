![img.png](img.png)

# Blocking I/O (블로킹 입출력):
- 블로킹 I/O는 작업이 완료될 때까지 프로그램이 대기하는 방식
- I/O 작업이 끝날 때까지 프로그램이 블로킹되어 있어 다른 작업을 수행할 수 없습니다.
- 전통적인 동기식 프로그래밍 모델에서 사용되며, 대부분의 입출력 작업은 블로킹 I/O 방식으로 동작합니다.  <br>
  예를 들어, 파일을 읽거나 쓰는 작업이나 네트워크에서 데이터를 받거나 전송하는 작업이 블로킹 I/O의 예시입니다.

# Non-Blocking I/O (논블로킹 입출력):
- 논블로킹 I/O는 작업을 시작한 후 완료 여부를 기다리지 않고 다른 작업을 수행하는 방식
- 작업이 완료되지 않더라도 프로그램이 블로킹되지 않고 다른 작업을 수행할 수 있습니다.
- 논블로킹 I/O를 사용하는 프로그램은 일반적으로 여러 작업을 동시에 처리하고, 작업이 완료될 때까지 주기적으로 상태를 확인.
- 주로 비동기식 프로그래밍 모델에서 사용되며, 대부분의 모던 I/O API에서 지원됩니다.  <br>
  예를 들어, 네트워크에서 데이터를 읽거나 쓰는 작업을 비동기적으로 수행할 수 있습니다.