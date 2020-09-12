- Javascript 연습문제
    - 리스트 안에 '딸기의 개수를 구하라'

    ```jsx
    let fruit_list = ['사과','감','감','배','포도','포도','딸기',
    '포도','감','수박','딸기']
    //map
    let count = 0
    fruit_list.map((value)=>{
    if (value == '딸기') count += 1
    })
    console.lod(count)

    //filter
    let count = fruit_list((fruit)=> fruit=="딸기")
    console.log(count.length)
    ```

    - 날씨 딕셔너리 데이터를 순회해, 특정 날씨 데이터 보이기
    - 날씨 데이터

        ```jsx
        const data = {
            "weatherData" : {
                "Thunderstorm": {
                    "iconName": "weather-lightning",
                    "gradient": ["#373B44", "#4286f4"],
                    "title": "천둥 번개가 치고 있어요!!",
                    "subtitle": "집에 있긔..."
                },
                "Drizzle": {
                    "iconName": "weather-hail",
                    "gradient": ["#89F7FE", "#66A6FF"],
                    "title": "이슬비가 내려요~",
                    "subtitle": "분위기 있게 내리는 중 🏳️‍🌈"
                },
                "Rain": {
                    "iconName": "weather-rainy",
                    "gradient": ["#00C6FB", "#005BEA"],
                    "title": "비가 내리고 있습니다 ☂️",
                    "subtitle": "밖에 비온다 주륵주륵 :)"
                },
                "Snow": {
                    "iconName": "weather-snowy",
                    "gradient": ["#7DE2FC", "#B9B6E5"],
                    "title": "눈이 내려와요",
                    "subtitle": "눈싸움 ㄱ? ☃️ "
                },
                "Atmosphere": {
                    "iconName": "weather-hail",
                    "gradient": ["#89F7FE", "#66A6FF"]
                },
                "Clear": {
                    "iconName": "weather-sunny",
                    "gradient": ["#FF7300", "#FEF253"],
                    "title": "화창한 날이에요",
                    "subtitle": "오늘 같은 날은 데이트...애인 있으면"
                },
                "Clouds": {
                    "iconName": "weather-cloudy",
                    "gradient": ["#D7D2CC", "#304352"],
                    "title": "구름이 많습니다!",
                    "subtitle": "우울해 하지말고 나가 놀기 ㅎ"
                },
                "Mist": {
                    "iconName": "weather-hail",
                    "gradient": ["#4DA0B0", "#D39D38"],
                    "title": "(엷은) 안개가 낀",
                    "subtitle": "뿌연 안개, 차조심! 🤚"
                },
                "Dust": {
                    "iconName": "weather-hail",
                    "gradient": ["#4DA0B0", "#D39D38"],
                    "title": "먼지가 많습니다, 미세먼지?",
                    "subtitle": "마스크 있죠?"
                },
                "Haze": {
                    "iconName": "weather-hail",
                    "gradient": ["#4DA0B0", "#D39D38"],
                    "title": "안개까 낀것 처럼 흐린 날...",
                    "subtitle": "흐리니 우울우울 하지말긔"
                }
          }
        }
        ```

    ```jsx
    let datas = data["weatherData"]
    let weather = (id) => 
    	Object.keys(datas).forEach((key) => {
    		if (key == id) console.log(datas[key])})
    ```

    - 이메일 판별하기

    ```jsx
    //이메일에 @와 .이 있는 지 판별
    let checkEmail = (email) => 
    	let eamils = email.split("")
    	if (email.indexOf('@')== -1 || email.indexOf('.')== -1) console.log("이메일이 아닙니다.")
    	else console.log("이메일이 맞습니다.")
    	
    //이메일 판별 정규식(JS)
    let regExp = /^[0-9a-zA-Z]([-_.]?[0-9a-zA-Z])*@[0-9a-zA-Z]([-_.]?[0-9a-zA-Z])*.[a-zA-Z]{2,3}$/i;
      // 검증에 사용할 정규식 변수 regExp에 저장

      if (emailVal.match(regExp) != null) {
        alert('Good!');
      }
      else {
        alert('Error');
      }
    };
    // / / 안에 있는 내용은 정규표현식 검증에 사용되는 패턴이 이 안에 위치함
    // / /i 정규표현식에 사용된 패턴이 대소문자를 구분하지 않도록 i를 사용함
    // ^ 표시는 처음시작하는 부분부터 일치한다는 표시임
    // [0-9a-zA-Z] 하나의 문자가 []안에 위치한 규칙을 따른다는 것으로 숫자와 알파벳 소문지 대문자인 경우를 뜻 함
    // * 이 기호는 0또는 그 이상의 문자가 연속될 수 있음을 말함
    ```

    map과 filter가 어렵고 딕셔너리를 자세히 들어가니 헷갈리기 시작했다. 무엇보다 간소화하는 방법이 보이는건 간결하지만 그만큼 더 많이 고민해야된다는 걸 깨달았다. ㅠ