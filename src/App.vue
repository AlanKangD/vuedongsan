<template>

  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
        <h4>상세페이지임</h4>
        <p>상세페이지내용임</p>
        <button v-on:click="모달창열렸니 = false"> 닫기</button>
    </div>
  </div>

  <div class="menu">
    <a v-for="작명 in 3" :key="작명">home</a>  <!--이렇게 쓰면 3번 home 이 반복됨-->
    
    <a v-for="i in 메뉴들" :key="i">{{i}}</a>  <!--하단의 메뉴들이라는 배열을 i에 담아주고 k는 반복할 때 꼭필요! {{ i }}-->


    <a v-for="(a, i) in 메뉴들" :key="i">{{i}}</a>  <!-- key를 써주지 않으면 에러를 발생 시키는데 반복을 돌릴때 인덱스 번호라고 생각하면됨-->
    <a v-for="(a, i) in 메뉴들" :key="i">{{a}}</a>  <!-- a를 출력하면 배열의 정보들이 들어가 있음-->                                          
  
  </div>

  <div>
        <img src="./assets/room1.jpg" class="room-in">

    <h2 @click="모달창열렸니 = true" :style="styleColor">{{oneroom[0].title}}</h2>
    <h4>{{oneroom[0].price}} 만원</h4>
    <p>가격 정보</p>
    <button v-on:click="신고수[0]++">허위매물신고</button> <span>신고 수 : {{신고수[0]}}</span>
    <!--이벤트 핸들러 생성  :: 실시간 렌더링이 되기 때문에 따로 자바스크립트를 선언하지 않고 변수에 값을 넣어도 자동 렌더링이 되기 때문에 
                          이런 형식으로 사용할 수 있습니다-->  

  </div>
  <div>
            <img :src="oneroom[1].image" class="room-in">

    <h2>{{oneroom[1].title}}</h2>
    <h4>{{oneroom[1].price}} 만원</h4>
    <p>가격 정보</p>
    <button v-on:mouseover="increase">허위매물신고</button> <span>신고 수 : {{신고수[1]}}</span>
    <!--mouseover 를 사용할 수도 있다.-->

    <!-- v-on 을 사용해서 안의 이벤트 핸들러라고 하고 이벤트를 사용할 수 있게 합니다.-->
  </div>
  <div>
            <img src="./assets/room2.jpg" class="room-in">

    <h2>{{products[2]}}</h2>
    <h4>{{price3}} 만원</h4>
    <p>가격 정보</p>
    <button @click="신고수[2]++">만족한 결과 출력</button> <span>좋아요  : {{신고수[2]}}</span>
  </div>
 
  <div v-for="(a , i) in products" :key="i">
    <h2>{{prices[i]}} 만원</h2>
        <h2>가격 정보</h2>
    <h4>{{a}}</h4>
        <hr/>
  </div>



</template>

<script>  
import roomdata from './assets/data.js';
export default {
  name: 'App',
  data() {
      return {
       모달창열렸니 : false, //모달창이 열렸는지 닫혔는지를 체크하는 boolean 상태의 변수 설정 
            //모달창 만드는 순서 1번째 

        메뉴들 : ['Home', 'Shop' , 'Abuout'],
        price1 : "100",
        price2 : "200",
        price3 : "300",
        prices : [100, 200, 300],
        products : ["역삼동원룸" , "천호동원룸" , "마포구원룸"], 
        styleColor  : "color : red;",
        backColor : "background-color : green",
        신고수 : [0,0,0],
        oneroom : roomdata,
      }
  },
  methods : {
    increase() {
      this.신고수[1] += 1; // 내부의 함수를 사용할 때는 this. 을 붙여 줘야 변수를 사용할 수 있습니다.
    }
  },
  components: {
    
    },
  
}
</script>

<style>
body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background-color: rgba(0, 0, 0, 0 ,5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
 
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
}

.menu {
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-in {
  width: 90%;
  margin-top: 40px;
}
</style>
