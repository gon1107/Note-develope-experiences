
1. 람다식은 편하다.
- new Function(param1, param2) {
    return result;
}
- ((param1, param2) -> result);
2. Utils는 오롯이 온전하여 전역에서 쓰는 클래스
- Common
- File
- IO
- String
- Url
3. Validator는 가변적이라 Utils가 아니다
4. Controller - Service - (BO(비즈니스 필요 데이터)) - DTO(전체 데이터) - DAO
- EntityController
- EntityService
- EntityForm
- Entity
- EntityRepository
5. interface를 쓰는 이유는 구조의 일관성을 위해서이며 interface명과 함수의 네이밍은 공통적이면서 가장 추상적으로 지은 뒤 실제 사용할 클래스의 이름으로 실현한다.
-> 초기에 함수를 충분히 추상적으로 지으면 인터페이스 필요없음
6. 상속은 문제가 있으며 해결방안은 합성, 인터페이스, 위임이다.
- why? 
  - 상속은 1:1 
  - 합성 : 클래스의 멤버변수로 들어감  
  - 인터페이스 : 공통적이며 추상적인 기능을 클래스에서 실현시킬 수 있게 해줌
  - 위임 : 합성된 클래스의 함수 사용
  - 합성은 하나의 클래스에 여러 멤버변수로 들어갈 수 있기 때문에 1:N
7. SOLID 개방 폐쇄 원칙 : 확장할 때는 개방, 수정할 때는 폐쇄
- if만 else는 구리다, 각각의 상황(if)을 클래스화시키고 add한 뒤 for()하면 된다.
- 하나의 기능에 변화가 생긴다고 전체 구조를 가진 코드를 바꾸지 않는다.
8. 상위 클래스의 기능을 하위 클래스가 변경시키는 건 구리다.(인터페이스를 쓰는 이유)
9. 코딩 규칙에 관하여(네이밍, 주석, 매개변수, 중첩코드 제거, 설명변수)
- 클래스의 이름을 멤버변수, 멤버함수에 포함시키지 마라.
- Context 정보에 포함된 단어는 매개변수명에 포함시키지 마라.
  - public void uploadUserAvatarImageToAWS(String userAvatarImageUri)
  - public void uploadUserAvatarImageToAWS(String ImageUri);
- 주석에 반드시 포함 (What, Why, how), 네이밍이 잘 돼 있다면 최소화
  - how : 코드 실행 순서
- 네이밍으로 기능을 추상화시켜서 리팩토링해라
- 함수의 매개변수가 5개 이상이라면 객체로 캡슐화해라
- 플래그 매개변수는 빈번하게 사용될 때만 준다.
  - function(bool isValid)
    - validfunction
    - function
- if에서 return을 넣음으로써 else를 최소화
- if 안의 내용이 길면 함수화
- 함수 시작할 때 첫줄에서 if return으로 예외처리
- 상수가 필요할 때 대문자로 구성된 설명변수에 넣어서 가독성 높이기
10. 단위테스트

