# Spring Boot 만들기
<br>
심심해서 만들었으며 이 글은 <b>Spring Tool Suite 4</b> 를 기준으로 작성 되었습니다.
<br>
<br>
<b>1. sts4를 실행한 뒤 왼쪽 상단의 File -> New -> Spring Starter Project 를 클릭한다.<br>
  Spring Starter Project 가 안보인다면 File -> New -> Other 을 클릭한 뒤 Wizards 아래의 텍스트 박스에 spring 이라고 검색한다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/125416774-4347d8e6-0ad9-4813-9826-e91a8e5b8438.png"/>
<br>
<br>
<br>
<b>2. 아래의 그림으로 설명한다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/125416907-70b4ec22-43ff-46c7-a2ca-cbde8cf45f1d.png"/>
<br>
- Service URL은 Spring Boot 패키지를 만들어주는 사이트이다. 기본으로 선택되어 있으니 넘어간다.
<br><br>
- Name 은 프로젝트 이름을 작성하면 된다.
<br><br>
- Name 바로 아래에 Use default location 이 자동으로 체크되어 있을텐데 이건 프로젝트 경로이다. 따로 지정하고 싶다면 체크를 풀고 선택하면 된다.
<br><br>
- Type 은 Maven, Gradle 중 선택 가능하다. 난 Maven을 사용하므로 Maven을 체크.
<br><br>
- Packaging 은 말 그대로 패키징을 뜻하는데 Jar와 War가 있을 것이다. Jar는 원본파일 그대로, War는 필요한 파일만 압축한다고 생각하면 이해하기 편하다. 실제로 이렇다는건 아니다
<br><br>
- Java Version 은 자바 버전으로 11이상을 권장한다. 내가 알기론 자바 11 이상에서 Spring Boot 가 되는걸로 알고 있다. (이 부분은 정확한건 아님)
<br><br>
- Language 는 언어. Kotlen, Groovy로도 작성이 가능한가보다. 난 안해봤다.
<br><br>
- Group 은 프로젝트 그룹이다. 아래에서 작성할 Package 를 같은 것 끼리 그룹으로 묶는 역할을 하는 것 같다. 아마도?
<br><br>
- Artifact 는 나도 모른다. 근데 Name 작성하면 알아서 작성될 것이다. 패스
<br><br>
- Version 은 말 그대로 버전인데 처음이니 그냥 그대로 냅두자
<br><br>
- Description 은 설명
<br><br>
- Working sets 는 나도 모른다. 그냥 넘어가자.
<br>
<br>
<br>
<b>3. 아래의 그림으로 설명한다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/125418240-93bddd22-074f-4de1-b8d2-6989f1fd5361.png"/>
<br>
- Spring Boot Version 은 버전마다 무슨 차이인지 잘 모르니 그냥 냅두자.
<br><br>
- Frequently Used 가 있는데 이건 Spring Boot로 패키지를 만들 때 일일히 찾아가면서 Maven Repository 뒤지지 말라고 넣어준 기능같다.<br>
  여기에 있는걸 체크하면 해당 기능이 활성화 된다. 진짜 아무것도 없이 웹에 Hello World 하나 찍을거라면 아무것도 안해도 되지만 우리는 웹 개발자 아닌가! 그렇다면 기본적으로 DB 연결은 필수 요소이니 MySQL Driver, 그리고 Spring을 사용하는데 어노테이션을 안쓸 수 있나? Getter Setter 일일히 하나하나 다 만들 순 없다. 그러므로 Lombok도 체크. 그리고 DB 와의 언어구문적? 연동을 쉽게 해주는 MyBatis. 이렇게 세 개는 아마 어디서 웹 개발을 하든 다 사용할 것이다. 무조건 체크해주자.<br>
  그리고 테스트 해 봤는데 위의 7개 요소 중 6개는 굳이 설정을 안해도 된다. MySQL Driver 하나 빼고.. 하지만 MySQL 설정까지 할거니 7개 다 체크하면 된다.
<br><br>
- Available 이라고 밑에 뭐 온갖게 쭉 있는데 쓸 사람만 체크해서 넣도록 하자. 그리고 Finish를 누르면 패키지가 만들어진다.
<br>
<br>
<br>
<b>4. 만들었으니 실행해볼텐데 오른쪽 아래의 초록색이 움직이고 있다면 조금 기다리자. 프로젝트를 생성하고 로딩중인 것이니..<br>
  완료 되었다면 실행해 보자! 실행 방법은 프로젝트 우클릭 -> Run As -> Spring Boot App 을 누르면 된다.</b>
<br>
<br>
<br>
<b>5. 아마 안될거다. 그리고 아래와 같은 오류가 뜰텐데 이는 위에서 말했듯이 MySQL Driver 는 설치했는데 연결을 안해줘서 그렇다.</b>
<br><br>
<img width="100%" src="https://user-images.githubusercontent.com/48707324/125419643-97c94959-8e39-458a-a532-c52a12ac4d6b.png"/>
<br>
<br>
<br>
<b>6. 그럼 이제 MySQL Driver 설정을 하자. 프로젝트에서 src/main/resources 를 열어보면 application.properties 라는 파일이 있다.<br>
  이걸 열어보면 아무것도 없을텐데 아래의 그림에서 DB주소와 username(id) 와 password 를 변경해서 넣어주면 된다.<br>
  물론 포트를 바꾸고 싶다면 첫 줄의 포트를 수정해도 된다. 그리고 앞에 #이 붙은건 주석처리 된 것이니 신경 안써도 된다.<br>
  3,4 라인의 구문은 jsp 파일의 루트 경로를 지정해준다고 생각하면 편하다.</b>
  
<br><br>
<img width="100%" src="https://user-images.githubusercontent.com/48707324/125420725-116850d1-6842-45bc-adb2-2ee9a4f0aef0.png"/>
<br>
<br>
<br>
<b>7. 다시 4번으로 돌아가 실행해보자. 오류가 안 나왔다면 인터넷 창을 열어 localhost:8080 이라고 주소창에 입력해본다.<br>
  그럼 무슨 에러 페이지라고 하나 나올텐데 그게 정상이다. 우린 아직 화면에 보여주는 것을 만들지 않았으니 말이다.</b>
  
<br>
<br>
<br>
<br>
<br>
<br>
<hr>
# Spring Boot 만들기 2탄!
<br>
여기부터는 MVC 구조로 진행되며 2탄에서는 
<br>
<br>
<b>1. 위의 포스팅까지 완료했다면 DB는 연결된 상태이다. 그러니 가져올 데이터를 만들어보자.<br>
공지글은 아니지만 테이블을 하나 만들어보자. 테이블의 필드값은 아래와 같이 만들면 된다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162144342-881de634-6105-47d4-a313-9112ab082a50.PNG"/>
<br>
<br>
<br>
<b>2. 테이블을 만들었다면 spring 툴로 돌아와서 본인의 패키지를 우클릭 하여 하위에 다른 패키지들을 생성한다.<br>
아래 이미지와 같은 구조로 생성하면 되고 처음 생성했을 경우 아이콘의 색상이 회색일 것이다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162148274-8a3c57d4-6e95-41b4-b772-31c11e09d5b5.png"/>
<br>
- 패키지를 만들 때 이름은 본인의 패키지명 뒤에 .controller 와 같은 식으로 적으면 된다. 아래는 예시
<br>
<br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162148749-8d64b0c7-84d2-49b7-9453-e526381e7c25.PNG"/>
<br>
<br>
<br>
<b>3. 패키지를 다 만들고 나면 아래 이미지와 같이 패키지 안에 클래스와 인터페이스를 생성해준다.<br>
src/main/resources 아래에 mapper 폴더와 noticeboardMapper.xml 파일이 있는데 이것도 나중에 필요하니 폴더와 파일을 생성해준다.<br>
클래스명을 변경하여 사용하고 싶은 경우 글 전체를 한번 읽어보고 본인에 맞게 수정하기 바란다.</b>
<br>
<br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162149119-e1d40ec4-989d-4425-be85-950266b9795e.PNG"/>
<br>
<br>
<br>
<b>4. 위에서부터 순서대로 가보자. DataAccessConfig.java는 아래와 같다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162162888-c61d7fad-7852-431e-a0ff-9ce658e25435.PNG"/>
<br>
- 세팅하는 부분이라 나도 자세히는 모른다. 자신의 패키지 명에 맞게 대충 바꿔넣자.
<br>
<br>
<br>
<b>5. DataSourceConfig.java</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162165985-5fef90e4-bf1c-4fe5-8192-294943db1b9d.PNG"/>
<br>
- 얘도 세팅하는 부분이라 잘 모른다. 그냥 적어놓자.
<br>
<br>
<br>
<b>6. 순서대로 가기로 했지만 MVC 패턴 부분은 있는 그대로 옮겨 적으면 잘 모르는 사람들은 빨간줄 막 떠서 뭐 잘못했나? 싶은 생각이 들 수도 있다.<br>
그렇기에 여기는 VO -> Service -> Mapper -> Impl -> Controller 순으로 설명하겠다. NoticeboardVO를 보자.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162167197-6bd24341-dbbc-499e-8b33-e0089e8b77c6.PNG"/>
<br>
- 클래스명 위에 @Getter @Setter가 보일 것이다. 이게 없으면 변수를 생성할 때 마다 getVar, setVar 과 같이 게터, 세터를 다 만들어줘야 한다.(롬복 짱)<br><br>
- 아래의 변수들은 DB에서 가져올 목록들이다. 변수 명은 DB 테이블의 이름과 동일하지 않아도 되지만 데이터 타입은 일치해야 한다. 즉, DB에서는 int로 정의한 것을 자바에서는 String으로 받을 수 없다는 말이다. 어쨌든 타입을 일치시킨다.
<br>
<br>
<br>
<b>7. 다음은 NoticeboardService.java 이다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162168479-77c7b2e9-666a-40f1-8c19-7117acab12ae.PNG"/>
<br>
- 얘는 클래스가 아니라 인터페이스로 되어 있는데 이 서비스를 구현하는건 Impl 파일에서 진행한다.
<br><br>
- 게시판에 글은 여러개일 것이므로 List 형식을 사용하여 가져온다.
<br>
<br>
<br>
<b>8. 다음은 NoticeboardMapper.java 이다. 6번에서 분명 Service -> Mapper 라고 했는데 왜 Mapper를 먼저 하느냐 하면 실제로 구현된 파일인 ServiceImpl은 Mapper 인터페이스가 정의되어 있지 않다면 에러가 나기 때문이다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162169827-2c5eca87-881d-44a3-a044-d89257d8c317.PNG"/>
<br>
- 얘는 구현된 파일인 ServiceImpl에서 사용할 때 쿼리문이 작성된 xml 파일을 매핑하는 친구이다.
<br>
<br>
<br>
<b>9. 다음은 noticeboardMapper.xml 이다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162171519-e9a4d01e-303b-4155-86b9-4d367db4fed0.png"/>
<br>
- 실제 쿼리문이 들어가는 파일이다. namespace 부분에는 인터페이스로 작성한 ~Mapper.java 파일을 패키지 경로와 함께 써준다.
<br><br>
- <select 라고 적혀있는 부분 옆 id는 ~Mapper.java 파일에서 작성한 메소드명을 작성한다.
<br><br>
- resultType 은 쿼리문을 돌리고 나서 나온 값을 어떤 형태로 넣을거냐 하는 것이다. select 구문에서 하나만 찾고자 하는 경우 int나 String 타입으로 지정이 가능하지만 우린 int와 String이 여러 개 있는 상태로 들고와야 하므로 클래스 타입으로 받는다. 받는 클래스 타입은 아까 작성한 VO 파일로 한다.
<br>
<br>
<br>
<b>10. 다시 Service 로 돌아와서 NoticeboardServiceImpl.java 이다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162172789-5951cda9-8ace-40af-b35a-82102c550db7.PNG"/>
<br>
- 클래스 위에 @Service 로 서비스 코드임을 명시하고 @Autowired 를 통해 ~Mapper.java 파일과 연결한다. 만약 @Autowired가 없다면 ~Mapper.java 파일의 경로를 일일이 작성해 주어야 한다.
<br><br>
- @Override 를 통해 인터페이스인 Service 코드를 구현한다.
<br>
<br>
<br>
<b>11. MVC 패턴의 마지막인 컨트롤러이다. NoticeboardController.java 파일의 코드는 아래와 같다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162178830-9617771d-2389-49b6-8827-4bfd5f88d794.PNG"/>
<br>
- Controller 라는 것을 명시하기 위해 클래스 위에 @Controller 라고 어노테이션을 작성한다.
<br><br>
- Impl 파일에서는 Mapper를 Autowired 하였다면 Controller 파일에서는 Service를 Autowired 한다.
<br><br>
- 로직 처리를 한다면 보통 여기서 많이 한다. 일단 별도의 로직은 없으므로 서비스 코드를 호출하여 리스트를 가져오고 가져온 리스트를 jsp 파일에서 보여주기 위해 model 이라는 객체에 addAttribute를 통해 데이터를 집어넣는다. addAttribute 는 매개변수를 2개를 가지는데 앞 부분은 String 으로 받는다. 뒷 부분은 Object로 받기에 뭘 넣어도 된다. String 이었던 앞의 매개변수는 jsp 파일에서 불러올 때 사용되는 문자이므로 임의로 지정하여도 상관 없다.
<br><br>
- return 으로 지정된 String 값은 아래에서 작성할 jsp 파일명이다. jsp 파일명을 다르게 할거라면 return 값도 다르게 작성하면 된다.
<br>
<br>
<br>
<b>12. 데이터 관련 작업은 끝났으니 사용자에게 보여질 jsp 파일을 작성해보자. 그 전에 경로는 아래와 같다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162179863-7d6e50b5-94f0-4835-af9a-f6a9eefc8473.png"/>
<br>
- 따로 건든게 없다면 src/main 까지만 있고 더 이상 파일이 없을텐데 새로운 폴더를 생성해서 저렇게 경로를 쭉 만든 다음 jsp 파일을 만든다.
<br>
<br>
<br>
<b>13. jsp 파일을 작성해보자. 코드는 아래와 같다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162181109-03fe06ff-d920-48a5-a277-3ae669bb18dc.PNG"/>
<br>
- 별 다른 내용은 없고 c:forEach 는 반복문을 뜻한다. items의 ${} 안 내용은 위에서 언급했듯이 Controller의 model.addAttribute에서 지정한 첫번 째 변수 값이다. ${}는 jsp에서 서버에서 나온 값을 인식하게 해 주는 문자라고 생각하면 된다. var 는 items를 어떻게 부를거냐 라는 것이고 varStatus는 반복문의 상태값을 어떻게 부를거냐 라는 것이다. 반복문의 횟수를 확인하고 싶다면 ${status.index} 와 같이 나타낼 수 있다.
<br>
<br>
<br>
<b>14. 끝! 인것 같지만 이대로 실행하면 안돌아간다. 설정 몇 가지를 추가해 주자. 프로젝트 최상위에 있는 pom.xml 파일의 <dependencies> 안에 아래의 내용을 추가한다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162182915-c2e0d004-7ee4-4f86-84c2-19cd515b40b7.png"/>
<br>
<br>
<br>
<b>15. 진짜 끝! 인것 같지만 spring session 문제로 안돌아갈 것이다. src/main/resources 아래의 application.properties를 열고 아래의 구문을 추가한다.</b>
<br><br>
spring.session.jdbc.initialize-schema=always
<br>
<br>
<br>
<b>16. 이제 실행해 보자. Controller에서 지정한 주소대로 입력한다. 이 글의 경우 localhost:8080/noticeboard 이다.<br>
물론 실행하면 아무것도 안뜰 수 있다. 이유는 DB에 데이터가 없기 때문이다. DB에 데이터를 임의로 집어넣고 실행해 보자. 아래와 같이 데이터가 나올 것이다.</b>
<br><br>
<img width="50%" src="https://user-images.githubusercontent.com/48707324/162183941-c91c738c-7668-4a9f-ae27-394c68fff14e.png"/>
