Lambda

```java
public static void main(String[] args) {
        Runnable r1 = () -> System.out.println("Hello World! 1");
        Runnable r2 = new Runnable() {
        @Override
        public void run() {
                System.out.println("Hello World! 2");
        }
};
r1.run(); // Hello World! 1
r2.run(); // Hello World! 2
```

Stream
1. 다량의 데이터를 일관성 있게 처리
2. 과거의 데이터 형태와 관계없이 같은 방식으로 다룰 수 있음
- Collection - List, Set의 상위 클래스
  - Stream이 정의돼 있음
  - 클래스를 구현한 List와 Set은 stream 호출 가능

```java
Map<Long, FileMatchingResultInfo> data = extractFileMatchingResultInfo(result);
String csvData = data.values().stream()
        .map(info -> toCsvString(info))
        .collect(Collectors.joining("\n"));
```