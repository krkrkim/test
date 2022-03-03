<template>
  <div class="home">
    <h1>Welcome to {{ title2 }}</h1>
    <input type="text" v-model="input1">
    <p>{{ input1 }}</p>
    <button type="button" @click="getData">Get</button>
    <button type="button" @click="setData">Set</button>
    <select name="" id="" v-model="region" @change="changeRegion">
      <option :key="i" v-for="(d,i) in options" :value="d.v">{{d.t}}</option>
    </select>

    <img v-bind:src="imgSrc" alt="">
    <img :src="imgSrc2" alt="">
    <div>
      <a :href="input1" target="_blank">{{ input1 }}</a>
    </div>
    <div>
      <!-- 
         red: input1==='apple' 
         클래스명 : 참/거짓
         
         자바스크립트 오브젝트 문법이기 때문에, 클래스명에 '-' 이 들어가면 홀따옴표로 쌓야됨.
       -->
      <h2 v-bind:class="{ red: input1==='apple', 'not-good': input1==='rice' }">원숭이는 {{ input1 }}을 좋아합니다.</h2>
    </div>
    
    <table v-if="tableShow">
      <!-- 
      v-if 는 렌더링 안함
      v-show는 렌더링은 하되 display:none 해버린거...
     -->
      <tr :key="i" v-for="(d,i) in options">
        <td>
          {{d.v}} 인덱스는 {{ i }}
        </td>
        <td>
          {{d.t}}
          <span v-if="d.t !== 'Seoul'">{{d.t}} - 수도아님</span> <!-- Seoul 아닐때만 출력 -->
          <span v-if="d.t == 'Seoul'">(대한민국수도)</span> <!-- Seoul 일때만 출력 -->
        </td>
        <td>
          <p :key="gu" v-for="gu in d.g" >{{ gu }}</p>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
 data() {
   return {
     title: "gemuse",
     title2: "Seoul",
     input1: "abc",
     region: "B",
     options: [
       {v:"S",t:"Seoul", g:['mapo-gu','jongro-gu','sedaemun-gu']},
       {v:"J",t:"Jeju", g:['segipo-si','jeju-si']},
       {v:"D",t:"Deagu", g:['seo-gu','dong-gu','jung-gu']},
       {v:"B",t:"Busan", g:['yeonje-gu','dongrae-gu']},
     ],
     tableShow:true,
     imgSrc:"https://placeimg.com/100/100/any",
     imgSrc2:"https://placeimg.com/150/150/any"
   }
 },
 watch: {
   input1(){
     console.log(this.input1);
   }
 },
 methods: {
   getData() {
     alert(this.input1);
   },
   setData() {
     this.input1 = "Daegu";
   },
   changeRegion(){
     alert(this.region);
   }
 },
 beforeCreate() {
   console.log("beforeCreate");
 },
 created() {
   console.log("created");
 },
 beforeMount() {
   console.log("beforeMount");
 },
 mounted() {
   console.log("mounted");
 },
 beforeUpdate() {
   console.log("beforeUpdate");
 },
 updated() {
   console.log("updated");
 },
 beforeUnmout() {
   console.log("beforeUnmout");
 },
 unmounted() {
   console.log("unmounted");
 },
}
</script>
<style scoped>
.red {
  color:red;
}
.orange {
  color:orange;
}
.aqua {
  color:aqua;
}
.not-good {
  color:gray;
}
</style>