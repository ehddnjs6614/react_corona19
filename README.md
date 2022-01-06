# Covid-19

## 개발목표 

`화제의 코로나 바이러스의 API 관련 클론 코딩이 있어서 호기심을 가지고 클론코딩을 해보았습니다. `

## 사용기술

 - React
 - axios
 - chart.js
 - react-chartjs-2
 - css 
  
  
  ## 주요기능
  
  - https://covid19api.com/ 에있는 오픈 API를 Axios로 사용
  - 불러온 API를 chart.js, react-chartjs-2 라이브러리를 활용해 화면에뿌려줌. 
  
  
  ***
  
  가져온 API 를 담을 각각의 State를 만들어놓는다
  
  ```
   const [confirmedData, setconfirmedData] = useState({
    labels: ['1월', '2월', '3월'],
    datasets: [
      {
        label: '국내 누적 확진자',
        backgroundColor: 'salmon',
        fill: true,
        data: [10, 5, 3],
      },
    ],
  })

  const [quarantineData, setQuarantineData] = useState({
    labels: ['1월', '2월', '3월'],
    datasets: [
      {
        label: '국내 누적 확진자',
        borderColor: 'salmon',
        fill: false,
        data: [10, 5, 3],
      },
    ],
  })

  const [comparedData, setComparedData] = useState({
    labels: ['1월', '2월', '3월'],
    datasets: [
      {
        label: '국내 누적 확진자',
        borderColor: 'salmon',
        fill: false,
        data: [10, 5, 3],
      },
    ],
  })
  ```
  
  ***
  
  (Axios로 API를 불러옴)
  
  ```
  useEffect(() => {
    const fetchEvents = async () => {
      const res = await axios.get(
        'https://api.covid19api.com/total/dayone/country/kr'
      )
      makeData(res.data)
    }
   ```
   
   ***
   
   
   react-chartjs-2라이브러리의  `Bar, Doughnut, Line` 활용해서 화면에뿌려준다.
   
   ```
   <section>
      <h2>국내 코로나 현황</h2>
      <div className="contents">
        <div>
          <Bar
            data={confirmedData}
            options={{
              title: {
                display: true,
                text: '누적 확진자 추이',
                fontSize: 16,
              },
            }}
          ></Bar>
        </div>
        <div>
          <Line
            data={quarantineData}
            options={{
              title: {
                display: true,
                text: '월별 격리자 현황',
                fontSize: 16,
              },
            }}
          ></Line>
        </div>

        <div>
          <Doughnut
            data={comparedData}
            options={{
              title: {
                display: true,
                text: `누적 확진 , 해제, 사망(${new Date().getMonth() + 1}월)`,
                fontSize: 16,
              },
            }}
          ></Doughnut>
        </div>
      </div>
    </section>
    ```
   
   ***
   
   ## 개선사항 & 느낀점
    - 부족한 UI 
    - 그외에 기능들
    
    클론코딩을 해보았는데 설명을들어도 이해가 안가는 부분은 따로 찾아봐서 익혀야겠다 
    모든 코드를 이해할순없지만 어떤흐름으로 동작하는지 체험해본거같다. 
   
   
   
   
  
