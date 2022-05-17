<template>
  <!-- 모달 -->
  <div class="black_bg" v-if="modal_state">
    <div class="white_bg">
      <h4>상세페이지</h4>
      <p>{{ room[idx].content }}</p>
      <span>신고수 : {{ room[idx].num }}</span>
      <button class="modal_close" @click="modal_state = false">X</button>
    </div>
  </div>

  <!-- 메뉴 -->
  <div>
    <nav class="menu">
      <!-- <a href="" v-for="menu in menus" :key="menu">{{ menu }}</a> -->
      <a href="" v-for="(menu, i) in menus" :key="menu">{{ menu }} {{ i }}</a>
    </nav>
  </div>


  <!-- <p>{{ now }}</p> -->


  <!-- 스타일 -->
  <!-- <img v-bind="item" v-bind:id="'thumb-' + item.id"> -->


  <!-- 트랜지션 -->
  <!-- <button @click="show = !show">변경하기</button>

  <transition name="slide-fade">
    <p v-if="show">Hello Vue.js</p>
  </transition> -->

  <!-- 클래스 -->
  <!-- <div :class="classObject">가나다라</div> -->


  <div v-for="(list, i) in room" :key="list.id" class="list">
    <div class="list_inner" @click="popOpen(i)">
      <img :src="list.image" class="room_img" alt="">
      <h4>{{ list.title }}</h4>
      <p>{{ list.price }} 만원</p>
    </div>
    <div class="list_bottom">
      <button @click="increase(i)">허위매물신고</button> 
      <span>신고수 : {{ list.num }}</span>
    </div>
  </div>

  <!-- 리스트 -->
  <!-- <div>
    <img :src="room[0].image" class="room_img" alt="">
    <h4 @click="modal_state = true">{{ room[0].title }}</h4>
    <p>{{ room[0].price }} 만원</p>
    <button @click="number[0]++">허위매물신고</button> <span>신고수 : {{ number[0] }}</span>
  </div>
  <div>
    <img :src="room[1].image" class="room_img" alt="">
    <h4 @click="modal_state = true">{{ room[1].title }}</h4>
    <p>{{ room[1].price }} 만원</p>
    <button @click="number[1]++">허위매물신고</button> <span>신고수 : {{ number[1] }}</span>
  </div>
  <div>
    <img :src="room[2].image" class="room_img" alt="">
    <h4 @click="modal_state = true">{{ room[2].title }}</h4>
    <p>{{ room[2].price }} 만원</p>
    <button @click="number[2]++">허위매물신고</button> <span>신고수 : {{ number[2] }}</span>
  </div> -->


</template>

<script>

import roomData from './data/post.js';

export default {
  name: 'App',
  data(){
    return {
      item: {
        id: 1,
        src: 'https://codingapple1.github.io/vue/room0.jpg',
        alt: '상품1의 섬네일',
        width: 200,
        height: 200,
      },
      classObject: {
        isChild: true,
        'is-active': false,
      },

      idx : 0,
      modal_state : false,
      modal_contents : '',
      // number : [0,0,0],
      menus : ['Home', 'Products', 'About'],
      // price : [60, 70, 90],
      // products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      room : roomData,
      show : true,
    }
  },
  computed: { //return값이 무조건 필요, 매개변수 전달 x, 꼭 사용해야할 시 아래와 같이 사용
    now(){
      return Date.now();
    },
    increase(){
      return (i) => {
        this.room[i].num++;
      }
    },
    popOpen() {
      return(index) => {
        this.idx = index;
        this.modal_state = true;
      }
    },

  },
  methods: { //아래 종속된 특정 함수가 실행되면 methods에 포함된 모든 함수가 실행됨 - 성능저하될 가능성 큼 - computed와 다른점.
    // increase(){
    //     this.number++;
    // }
    // increase(i){
    //   // this.number[i]++;
    //   this.room[i].num++;
    // },
    // popOpen(index) {
    //   this.idx = index;
    //   this.modal_state = true;
    // }
  },
  components: {
  }
}

</script>

<style lang="scss">
@import '~@/assets/scss/common';
</style>
