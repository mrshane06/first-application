<template lang="">
  <div>
    <h1>Counter -> <span>{{Counter}}</span></h1>
    <button v-on:click="increment()">Increment</button> 
    <!-- instead of using v-on:click , you can use @click...same thing...Only for Events -->
    <img v-bind:src="imgUrl"> <!--  a shorter way to replace v-bind is just to place the colon (:)...Only for Imgaes -->
    <button v-on:click="decrement()">decrement</button>
     
    <!-- Class styling binding -->
    <h4 :class="{hello:check}">Conditional Rendering</h4>

     <div>
      <h1 v-if="check">The value is True</h1>
      <h1 v-else>The value is false</h1>
      <button @click="change">change state</button>
      <h1 v-show="check">This is the v-show element</h1>
    </div>
    <!-- <info-comp first-name="hehe" last-name="HEHEHEHE"/>
    <info-comp first-name="MWAHAHA"/>
    <info-comp :object-data='singleObject'/>  -->
    <info-comp>
      Hehe I am using slots
    </info-comp>
    <div>
      <ul>
        <!-- <li v-for="sport in sports" :key='sport'>{{sport}}</li>  Origin code for the array -->
        <li v-for="({message},index) in objects" :key='index'>{{message}}</li>
      </ul>
      <!-- one way data binding -->
      <h3>{{oneWayText}}</h3>
      <!-- two way data binding -->
      <h3>{{twoWayText}}</h3>
      <input type="text" v-model="twoWayText">
     </div>
  </div>

  <slot-comp>
    <template #slotTitle> <!--the name is v-slot , but can be replaced by #-->
      Card Slot
    </template>
    <template #default>
      <img :src="imgUrl">
    </template>
  </slot-comp>


</template>
<script>
import InfoComp from '../components/InfoComp.vue'
import SlotComp from '../components/SlotsComp.vue'
export default {
  data(){
    return{
      Counter:0,
      imgUrl:'https://images.ctfassets.net/hrltx12pl8hq/28ECAQiPJZ78hxatLTa7Ts/2f695d869736ae3b0de3e56ceaca3958/free-nature-images.jpg?fit=fill&w=1200&h=630',
      check:true,
      sports:['soccer','netball','volleyball'],
      objects:[
      {message:'Hello There1',id:1},
      {message:'Hello There2',id:2},
      {message:'Hello There3',id:3}
    ],
    singleObject:{
      name:'Gwiba',
      surname:'Mabandla'
    },
    oneWayText:'ONE WAY',
    twoWayText:'TWO WAY'
    }
  },
  components:{
      InfoComp,
      SlotComp
    },
  methods:{
    increment(){
      this.Counter++
    },
    decrement(){
      this.Counter--
    },
    change(){
      this.check = !this.check
    }
  }
}
</script>
<style scoped>
  h1{
    color:blue
  }
  
  img{
    width: 250px;
    height: 250px;
    transition: 2s;
    padding: 10px;
  }

  img:hover{
    transform: rotate(3600deg);
  }

  .hello{
    color: orangered;
  }
</style> 