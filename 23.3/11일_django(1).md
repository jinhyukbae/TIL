# Django

## settings.py
* 프로젝트를 운영하는데 필요한 설정들이 들어가 있는 파일 

## urls.py
* 사용자가 접속하는 path에 따라서 요청을 어떻게/누가 처리 해줄 것인가를 지정하는 파일 (라우팅)

## manage.py
* 프로젝트를 진행하는데 필요한 여러가지 기능이 들어간 유틸리티 파일

![image](https://user-images.githubusercontent.com/115385678/224487325-6931e3ef-a437-4c3e-8524-f14844a4e9fa.png)
* api를 프로젝트 안에서 구현하는 것이 아니라 app 이라는 더 작은 단위로 만들어서 그 안에서 실제 구현을 하게 된다.  

![image](https://user-images.githubusercontent.com/115385678/224487373-871c04b2-3947-45cd-ae32-dc2b4c22c8f0.png)
* 프로젝트를 하다보면 복잡해질 수 있는데 서로 연관된 로직들을 모아서 그룹핑 해야한다. 이때 여러개의 app들을 만들어서 정리정돈 하게 된다.

![image](https://user-images.githubusercontent.com/115385678/224487440-0c86f07c-05bb-4cf5-aa48-a2b80133eecc.png)
* 그 앱 안에는 view 라는 것이 만들어지고 함수를 만들어서 api 구현들을 view 안에서 함수로 해나가게 된다.

![image](https://user-images.githubusercontent.com/115385678/224487498-6405349e-cd8b-4439-81cc-c3d900f53c02.png)
* 사용자가 여러가지 경로로 접속을 함 -> 그 경로를 누구에게 위임할 것인가를 urls.py을 수정해서 코딩

![image](https://user-images.githubusercontent.com/115385678/224487549-f92ade5a-22a8-46f6-9e5b-67c9c1371a12.png)
* 프로젝트 urls.py에서 더 작은 단위인 app에 urls.py에 위임

![image](https://user-images.githubusercontent.com/115385678/224487585-4a8e946f-45e5-411b-8762-8069bb0b32f2.png)
* 위와 마찬가지로 app에 urls.py에서 작성한 코드에 의해서 view에 함수에 위임

![image](https://user-images.githubusercontent.com/115385678/224487846-bb558ef2-ae25-40b2-8f3c-e082a2edb04d.png)
* 장고는 DB에 직접 접속하지 않고 model을 통해서 사용  
* DB의 정보를 받아서 클라이언트에 응답
  * 그 결과로 html json xml 같은 형태의 데이터를 만들어서 사용자에게 보내게 된다.
