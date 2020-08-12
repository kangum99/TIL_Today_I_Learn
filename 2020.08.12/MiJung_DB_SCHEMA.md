- WEB DB SCHEMA
    - 참고 사이트

    [관계형 데이터베이스 설계 및 구축](https://advenoh.tistory.com/31)

    DB초기 설계는 중요! 잘못 설계 시 현재 사용중인 구조를 나중에 쉽게 변경하기 어렵+ 일관성, 무결성 유지안될수 있는 문제가 생긴다.

    - 관계형 DB 설계 방법 2가지
        - E-R모델과 릴레이션 변환 규칙을 이용한 설계(내가 쓸것)
        - 정규화를 이용한 설계
            - 이상현상을 제거, 중복 최소화, 작은 릴레이션화
    - E-R모델과 릴레이션 변환 규칙을 이용한 설계방법
        1. 데이터 요구사항에 대한 분석(요구사항 명세서)
        2. 개념 스키마 설계(ERD)
        3. 논리 스키마 설계(릴레이션 스키마의 테이블 명세서)
        4. 내부 스키마 설계(DB스키마생성 SQL문)

    ---

    ### 1. 요구사항 분석하기

    - **쿠기 브라우저** 사용-name, value, expires, domain, path
    - 지역검색을 도, 시 , 동&면, 으로 나눠서 고를 수 있게 한다. (정보는 geo API) - 중복가능
    - 고른 후 주소를 기반으로 음식점들을 사용자 지정 갯수만큼 랜덤으로 뽑아온다. (정보는 search 지역 API)
    - 여기서 음식점 이미지는 (search 검색어 image API)에서 음식점 이름과 지역을 검색한 것을 랜덤으로 가져온다.
    - **랜덤 선택 시 사용자가 like를 한 음식점에 대한 정보를 넣는다. like를 못받으면 단계별로 지운다**..?
    - **랜덤 선택에 대한 랭크테이블이 필요하다. 최종적으로 Yes를 받은 음식점을 랭크에 넣거나 like값을 올려준다.**
    - **카테고리 선택 시 이용자가 새로운 카테고리를 만들 때 지역별로 테이블이 필요하다. (첫화면에서 지역별로 카테고리 보여줄 예정)**
    - **카테고리 선택 시 이용자가 like를 한 음식점에 대한 정보를 넣는다. like를 못받으면 지운다.**
    - **카테고리 선택에 대한 랭크 테이블이 필요하다. 최종적으로 Yes를 받은 음식점을 랭크에 넣거나 like값을 올려준다.**

    ### 2. 개념적 설계로 E-R다이어그램 만들기

    - cookie - name, value, expires, domain, path
    - random_like(user) - name, Y/N, link, address, category_food, image
    - random_rank - rank, name, like, link, address, category_food, image
    - category_area - area, category_main, password
    - category_usermade - category_main, name, like, link, address, category_food, image, area
    - category_like(user) - category_main, name, Y/N, link, address, category_food, image
    - category_rank - category_main, rank, name, like, link, address, category_food, image

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2e70996d-51d5-4401-98af-5b27c5acf1e2/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/2e70996d-51d5-4401-98af-5b27c5acf1e2/Untitled.png)

    like가 1개만 선택해서 rank에 올리는 건 무조건 하나 또는 없음이므로 like(일 필수) , rank(일 선택)

    area가 usermade를 여러개갖거나 안갖을 수 있고, uesrmade는 area를 무조건 하나만 꼭 가져야되므로 area(다 선택), usermade(일 필수)

    ### 3. 논리적 설계로 릴레이션 스키마, 테이블 명세서

    - cookie - **name**, value, expires, domain, path
    - random_like(user) - **name+area**, Y/N, link, address, category_food, image
    - random_rank - **rank**, name+area(FK), like, link, address, category_food, image
    - category_area(area) - area, **category_main**, **password**
    - category_usermade(category) - **category_main(FK)**, **name+area**, like, link, address, category_food, image, area
    - category_like(user) - category_main(FK), **name+area**, Y/N, link, address, category_food, image
    - category_rank - category_main, **rank**, name+area(FK), like, link, address, category_food, image

    > **키가 이게 맞는건지 잘 모르겠다...ㅎ**

    ### 4. 물리적 스키마 및 구현

    ![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dfca85ff-38b2-4ad2-8366-4c08c00abe6b/db.jpg](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/dfca85ff-38b2-4ad2-8366-4c08c00abe6b/db.jpg)

    > 데이터 베이스를 배운지 시간이 지나서.. 이렇게 하는게 맞나 긴가민가하다.. 프로젝트를 실제로 하면 많이 오류가 날거같다. ㅎ