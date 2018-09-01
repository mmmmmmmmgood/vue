<template>
  <div id="app">
    <img src="./assets/logo.png">
    <HelloWorld/>
    <div>
      {{testDemo}}
    <input v-model="inputVal" />
    <template v-if="flag">1</template>
    <div v-for="(value, key) in dataArr" :key="key" @click="fns(key)" :class="{done:value.done}">
        {{value.title}},{{key}}
    </div>
    <button v-on:click="clickBtn">add</button>
    {{comMain}}/{{dataArr.length}}
    <button v-on:click="clean">clean</button>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data(){
    return {
       testDemo:'123',
        flag:true,
        dataArr:[{title:'one',done:false},{title:'two',done:false},{title:'three',done:false}],
        inputVal:''
    }
  },
  methods:{
      clickBtn(){
          this.dataArr.push({title:this.inputVal,done:false});
          this.inputVal="";
      },
      fns(key){
        this.dataArr[key].done=!this.dataArr[key].done
      },
      clean(){
        this.dataArr=this.dataArr.filter(v=>v.done==false)
      }
  },
  computed:{
    comMain(){
      return this.dataArr.filter(v=>v.done==false).length;
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.done{color:red;}
</style>
