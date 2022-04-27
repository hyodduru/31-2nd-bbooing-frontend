<h1>BBooing Term Project</h1>
<h2>Introduction</h2>


* 프로젝트 진행 기간 : 4월 11일 ~ 4월 22일
* 프로젝트 주제 : 커머스 웹사이트 클론 코딩하기 
* 클론 코딩한 웹사이트 : 탈잉 https://taling.me/
* 구성 : Front-end 4명(구본희, 김정수, 김효정, 임재혁) Back-end 2명(류미류, 이강호)
* 프로젝트 웹사이트 링크 : http://bbooingbbooing.s3-website.ap-northeast-2.amazonaws.com/


<h2>Demo</h2>

![다중필터](https://user-images.githubusercontent.com/90507720/164960426-2560f9c1-da25-4a5b-8999-cfd90e8b2bd0.gif)


![IMG_1253](https://user-images.githubusercontent.com/90507720/164960399-29d11671-2b7c-46a5-87e9-32f4d86332c2.jpg)

![상세페이지](https://user-images.githubusercontent.com/90507720/164960411-311e1206-3585-43a0-869c-9ca2b72c30fe.gif)


![리뷰](https://user-images.githubusercontent.com/90507720/164960414-e033959a-d3a9-421f-ade2-5b629cf8a003.gif)
![검색](https://user-images.githubusercontent.com/90507720/164960417-7355de31-7175-4d78-b305-f4c2f6ae91a1.gif)
![vod](https://user-images.githubusercontent.com/90507720/164960447-d3ebcaef-a017-4969-b352-a5a89ffcf30c.gif)

<h2>Technologies</h2>

* 공통 : Git, github, git rebase 
* Front-End : ReactJS, Styled-Component
* Back-End : Python, Django web

<h2>구현 기능</h2>

#### 1. 소셜 로그인 / 회원가입 (카카오톡) 

- SDK방식으로 카카오 API활용한 소셜 로그인 구현
- 로그인시 카카오 토큰/ 사용자 정보(프로필사진/닉네임) localStorage에 저장


#### 2. nav 바 검색기능 구현
- navigate, query string, useLocation().search 활용 

#### 3. 메인 페이지 

- 리액트 슬릭 라이브러리를 
활용한 슬라이더 구현

- 찜 기능 구현
(fetch - post 활용)


#### 4. 강좌 리스트 페이지 

- 쿼리 파라미터를 활용한 기능 구현 
    - 다중필터
    - 페이지네이션

- custom hook 활용 - useOutSideClick (필터 카테고리 바깥 dom을 클릭을 감지해주는 커스텀 훅) - 바깥 dom 클릭시 해당 필터 체크리스트가 보이지 않게끔 한다. 

#### 5. 위시리스트(찜)

- 좋아요 버튼 클릭시 데이터베이스로 해당 위시리스트 상품 전송. 페이지를 새로고침 했을 때도 좋아요 버튼 클릭 상태 유지
- custom hook 활용 - useWishList (위시리스트 목록을 받아와 해당 값을 return하는 커스텀 훅)  - 자주 쓰이는 함수 커스텀 훅으로 만들기
- 위시리스트 페이지에서는 데이터베이스로 전송했던 상품 목록들을 받아볼 수 있다. (fetch - get 활용)

#### 5. 리뷰

- 상품 상세 페이지 내 해당 상품에 대한 리뷰 컴포넌트 구현
- formData.append를 활용하여 이미지 업로드 기능 구현 
- 리뷰 작성 및 삭제 기능 (fetch - post, delete)

#### 6. VOD main 
- video 태그를 이용한 슬라이더와 프로필이미지 슬라이더 두개를 react-slick 라이브러리 asNavFor API 를 활용하여 연결된 하나의 슬라이더 구현

<h2>내가 담당한 부분</h2>
메인 페이지와 강좌 리스트 레이아웃 및 페이지네이션 다중필터 기능 구현, nav 바 검색기능 구현, 위시리스트(찜, 좋아요 기능), 리뷰 이미지 업로드 기능

#### 1. 메인 페이지
- 메인 페이지에서 가장 기억에 남는 건 react slick 라이브러리를 활용하여 슬라이더 기능을 구현
- 좋아요(찜) 기능 구현 (fetch -post)
- 좋아요 개수 바로 업데이트 기능 구현(state 끌어올리기)
- custom hook을 활용하여 찜 목록 가져오는 함수 만듬(useWishList)
- navigate를 활용하여 태그들 클릭 시 해당 상세 페이지로 이동하는 기술 추가 

#### 2. nav 검색기능 - query string 
- 어느 페이지에서든 고정적으로 존재하는 nav바에서 검색할 경우 상세페이지로 이동하여 검색한 결과들에 대한 정보를 얻는 기능 구현
- navigate를 활용하여 상품리스트 페이지로 이동한 뒤, 거기서 useLocation().search를 활용하여 검색 값을 얻어 해당 정보를 데이터베이스로 요청을 하는 로직 구현 

#### 3. 강좌리스트 페이지 - query string 활용한 다양한 기능 구현
- 다중 필터 기능 구현 
   - useLocation().search, useEffect, useState, navigate 활용

   - 필터 적용이라는 버튼을 누를 때마다 체크된 리스트로 쿼리스트링을 만들고 navigate를 이용하여 해당 url로 이동을 한다. 
   - 카드 정보를 얻는 함수의 의존성 배열에 useLocation().search를 넣어줌으로써 url이 변경할 때마다 필터된 정보를 요청하도록 함. <br />
- pagination 기능 구현 (12개 씩 정보 요청)
pagination을 위해 필요한 offset과 limit 값을 state로 관리를 해주고 해당 값이 변할 때마다 리렌더링이 일어날 수 있도록 함.
또한 pagination 버튼은 요청해서 받아온 정보가 12개 일 때 (12개가 최대) 또는 두번째 페이지가 되었을 때 보이게끔 조건식을 걸어두었다. <br />
- useOutSideClick custom hook 활용 
외부 dom 바깥을 감지해주는 useOutSideClick이라는 custom hook도 만들어 카테고리 부분 바깥을 눌렀을 때 체크리스트가 보이지 않게끔 기능 구현을 해주었다.

#### 4. 리뷰 이미지 업로드 기능 
- formData.append()를 활용하여 이미지와 글을 함께 업로드하는 기능 구현
<h2>Reference</h2>

* 이 프로젝트는 탈잉 사이트를 참조하여 학습목적으로 만들었습니다.
* 실무수준의 프로젝트이지만 학습용으로 만들었기 때문에 이 코드를 활용하여 이득을 취하거나 무단 배포할 경우 법적으로 문제될 수 있습니다. 


