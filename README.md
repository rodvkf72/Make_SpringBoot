# Spring Boot 만들기
<br>
<stroke>심심해서 만듬</stroke>
<br>
<br>
이 글은 <b>Spring Tool Suite 4</b> 를 기준으로 작성 되었습니다.
<br>
<br>
1. sts4를 실행한 뒤 왼쪽 상단의 File -> New -> Spring Starter Project 를 클릭한다. Spring Starter Project 가 안보인다면 File -> New -> Other 을 클릭한 뒤 Wizards 아래의 텍스트 박스에 spring 이라고 검색한다.
<br>
![image](https://user-images.githubusercontent.com/48707324/125416774-4347d8e6-0ad9-4813-9826-e91a8e5b8438.png)
<br>
<br>
<br>
2. 아래의 그림으로 설명한다.
<br>
![image](https://user-images.githubusercontent.com/48707324/125416907-70b4ec22-43ff-46c7-a2ca-cbde8cf45f1d.png)
<br>
Service URL은 Spring Boot 패키지를 만들어주는 사이트이다. 기본으로 선택되어 있으니 넘어간다.
<br>
Name 은 프로젝트 이름을 작성하면 된다.
<br>
Name 바로 아래에 Use default location 이 자동으로 체크되어 있을텐데 이건 프로젝트 경로이다. 따로 지정하고 싶다면 체크를 풀고 선택하면 된다.
<br>
Type 은 Maven, Gradle 중 선택 가능하다. 난 Maven을 사용하므로 Maven을 체크.
<br>
Packaging 은 말 그대로 패키징을 뜻하는데 Jar와 War가 있을 것이다. Jar는 원본파일 그대로, War는 필요한 파일만 압축한다고 생각하면 이해하기 편하다.
<br>
Java Version 은 자바 버전으로 11이상을 권장한다. 내가 알기론 자바 11 이상에서 Spring Boot 가 되는걸로 알아서(이 부분은 정확한건 아님)
<br>
Language 는 언어. Kotlen, Groovy로도 작성이 가능한가보다. 난 안해봤다.
<br>
Group 은 프로젝트 그룹이다. 아래에서 작성할 Package 를 같은 것 끼리 그룹으로 묶는 역할을 하는 것 같다. 아마도?
<br>
Artifact 는 나도 모른다. 근데 Name 작성하면 알아서 작성될 것이다. 패스
<br>
Version 은 말 그대로 버전인데 처음이니 그냥 그대로 냅두자
<br>
Description 은 설명
<br>
Working sets 는 나도 모른다. 그냥 넘어가자.
<br>
<br>
<br>
3. 아래의 그림으로 설명한다.
<br>
![image](https://user-images.githubusercontent.com/48707324/125418240-93bddd22-074f-4de1-b8d2-6989f1fd5361.png)
<br>
Spring Boot Version 은 버전마다 무슨 차이인지 잘 모르니 그냥 냅두자.
<br>
Frequently Used 가 있는데 이건 Spring Boot로 패키지를 만들 때 일일히 찾아가면서 Maven Repository 뒤지지 말라고 넣어준 기능같다. 여기에 있는걸 체크하면 해당 기능이 활성화 된다. 진짜 아무것도 없이 웹에 Hello World 하나 찍을거라면 아무것도 안해도 되지만 우리는 웹 개발자 아닌가! 그렇다면 기본적으로 DB 연결은 필수 요소이니 MySQL Driver, 그리고 Spring을 사용하는데 어노테이션을 안쓸 수 있나? Getter Setter 일일히 하나하나 다 만들 순 없다. 그러므로 Lombok도 체크. 그리고 DB 와의 언어구문적? 연동을 쉽게 해주는 MyBatis. 이렇게 세 개는 아마 어디서 웹 개발을 하든 다 사용할 것이다. 무조건 체크해주자. 그리고 테스트 해 봤는데 위의 7개 요소는 다 체크하고 돌려도 설정을 굳이 안해도 된다. MySQL Driver 하나 빼고..
<br>
Available 이라고 밑에 뭐 온갖게 쭉 있는데 쓸 사람만 체크해서 넣도록 하자. 그리고 Finish를 누르면 패키지가 만들어진다.
<br>
<br>
<br>
4. 만들었으니 실행해볼텐데 오른쪽 아래의 초록색이 움직이고 있다면 조금 기다리자. 프로젝트를 생성하고 로딩중인 것이니.. 그리고 실행해 보자! 실행 방법은 프로젝트 우클릭 -> Run As -> Spring Boot App 을 누르면 된다.
<br>
<br>
<br>
5. 아마 안될거다. 그리고 아래와 같은 오류가 뜰텐데 이는 위에서 말했듯이 MySQL Driver 는 설치했는데 연결을 안해줘서 그렇다.
<br>
![image](https://user-images.githubusercontent.com/48707324/125419643-97c94959-8e39-458a-a532-c52a12ac4d6b.png)
<br>
<br>
<br>
6. 그럼 이제 MySQL Driver 설정을 하자. 프로젝트에서 src/main/resources 를 열어보면 application.properties 라는 파일이 있다. 이걸 열어보면 아무것도 없을텐데 아래의 그림에서 DB주소와 username(id) 와 password 를 변경해서 넣어주면 된다. 물론 포트를 바꾸고 싶다면 첫 줄의 포트를 수정해도 된다. 그리고 앞에 #이 붙은건 주석처리 된 것이니 신경 안써도 된다.
<br>
![image](https://user-images.githubusercontent.com/48707324/125420725-116850d1-6842-45bc-adb2-2ee9a4f0aef0.png)
<br>
<br>
<br>
7. 다시 4번으로 돌아가 실행해보자. 오류가 안 나왔다면 인터넷 창을 열어 localhost:8080 이라고 주소창에 입력해본다. 그럼 무슨 에러 페이지라고 하나 나올텐데 그게 정상이다. 우린 아직 화면에 보여주는 것을 만들지 않았으니 말이다.
