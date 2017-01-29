<template>
    <div id="Counter">
      <div id="myCount">Score:<b>{{ displayedValue }}</b></div>
      </br>
      <button v-on:click="up()">Up</button>
      <button v-on:click="down()">Down</button>
      <input type="text" v-model="newValue">
      <button v-on:click="set()">Set</button>
      <button v-on:click="reset()">Reset</button>
      <hr>
    </div>
</template>

<script>
export default {
  name: 'Counter',
  data () {
    return {
      currentValue:this.value,
      currentFormat:this.format,
      newValue:0,
    }
  },
  props: ["value","format","id"],
  methods:{
    up(){
      if(this.currentValue < Math.pow(10,this.currentFormat)-1){
        this.currentValue++;
      }
    },
    down(){
      if(this.currentValue>0){
        this.currentValue--;
      }
    },
    set(){
      if(this.newValue > Math.pow(10,this.currentFormat)-1 || this.newValue<0)
      {
        alert('Błąd! Podano nieprawidłowe dane!');
      }
      else{this.currentValue=this.newValue;}
    },
    reset(){
      this.currentValue=0;
    },
},
  computed:{
    displayedValue(){
      return new Array(this.currentFormat-(this.currentValue+"").length+1).join(0)+this.currentValue;
    }
  }

}


</script>

<style>
#Counter{
  margin-top: 30px;
  width:80%;
  margin-left: 10%;
  text-align: center;
  font-weight: bold;
  color: #3f0f0c;
  font-size: 1.3em;
}

#myCount{
  font-size: 1.6em;
  padding-bottom: 2px;
}

button {
    width: 80px;
    background-color: #7F1E19;
    border-radius: 10px;
    color: white;
    border: none;
    height: 40px;
    margin: 0 10px 0 10px;
    cursor: pointer;
}
button:hover {
    background-color: #3f0f0c;
}

input[type="text"] {
    width: 200px;
    height: 40px;
    border: none;
    border-radius: 10px;
    padding: 0 10px 0 10px;
    font-weight: bold;
    color: #3f0f0c;
    font-size: 1.3em;
    text-align: center;
}
</style>
