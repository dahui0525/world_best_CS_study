# Collection
- 모든 값을 메모리에 저장하는 자료구조다. 따라서 Collection에 추가하기 전에 계산이 완료되어 있다.
- 외부 반복을 통해 사용자가 직접 반복 작업을 거쳐 요소를 가져올 수 있다. <br> ex) (for-each)

# Stream
- Collection에 요청할 때만 요소를 계산한다. 
- 내부 반복을 사용하므로, 추출 요소만 선언해주면 알아서 반복 처리를 병렬 연산으로 진행한다.
- 스트림에 요소를 따로 추가 혹은 제거하는 작업은 불가능하다.
- 원본의 데이터를 변경하지 않는다.
- 일회용이다.

## 공통점과 차이점
Stream과 Collection 둘 다 연속된 요소 형식의 값을 저장하는 자료구조의 인터페이스를 제공한다. <br>
연속된이란, 순서와 상관없이 아무 값에나 접속하는 것이 아닌 순차적으로 접근한다는 것을 의미한다.  <br>
스트림과 컬렉션의 핵심적인 차이는 데이터를 언제 계산하느냐이다.

### Stream의 연산 과정
- 스트림은 연산 과정이 '중간'과 '최종'으로 나누어진다.
- filter, map, limit 등 파이프라이닝이 가능한 연산을 중간 연산, count, collect 등 스트림을 닫는 연산을 최종 연산이라고 한다.
- 둘로 나누는 이유 : 중간에 연산을 하는 것이 아닌 최종 연산에서 모두 병합하여 한 번에 계산하기 위해서.

ex) Item 중에 가격이 1000 이상인 이름을 5개 선택한다.
```
List<String> items = item.stream()
    			.filter(d->d.getPrices()>=1000)
                          .map(d->d.getName())
                          .limit(5)
                          .collect(toList());
```                          
filter와 map은 다른 연산이지만, 한 과정으로 병합된다.  <br>
Collection 이었다면 가격이 1000 이상인 아이템을 찾아내서 이름만 따로 저장하는 중간 연산을 거친 다음 5개를 선택해야 한다.


### 중간 연산
1. Stream 필터링 : filter(), distinct()
2. Stream 변환 : map(), flatMap()
3. Stream 제한 : limit(), skip()
4. Stream 정렬 ; sorted()
5. Stream 연산 결과 확인 : peek()

### 최종 연산
1. 요소의 출력 : forEach()
2. 요소의 소모 : reduce()
3. 요소의 검색 : findFirst(), findAny()
4. 요소의 검사 : anyMatch(), allMatch(), noneMatch()
5. 요소의 통계 : count(), min(), max()
6. 요소의 연산 : sum(), average()
7. 요소의 수집 : collect()

### StreamAPI의 장점
스트림 API를 사용하면 데이터에 대한 반복 처리를 내부에서 처리해주기 때문에, 
개발자는 간단한 메서드 체이닝을 통해 데이터를 처리할 수 있다.
이는 코드의 가독성을 향상시키고 작업을 더욱 효율적으로 만들어준다.

### 면접 질문
- **Stream API란 무엇인가요?** <br>
Stream API란 자바에서의 일련의 데이터 요소인 배열이나 컬렉션 등의 데이터를 처리하기 위한 API 입니다. <br>
Stream API의 특징은 멀티 스레드를 활용해서 병렬로 연산을 수행할 수 있고, 내부 반복으로 연산을 수행하기 때문에 코드가 매우 간단해진다는 것을 알 수 있습니다.