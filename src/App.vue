<template>
  <div id="app">
    Value: <input type="text" v-model="value" />
    Format: <input type="text" v-model="format" />
    <button @click="add()">Add</button>
    <button @click="deleteMe()">Delete</button>
  <hr>
    <transition-group name="list">
      <counter v-for="Counter in counters" class="list-item" :value="Counter.value" :format="Counter.format" :key="Counter.id"></counter>
    </transition-group>
  </div>
</template>

<script>
import Counter from './Components/Counter.vue'
export default {
  name: 'app',
  data () {
    return {
        value:0,
        format:1,

      counters: [ { value:5,
                    format:4,
                    id:Math.random(),
                  },
                  { value:6,
                    format:3,
                    id:Math.random(),
                  },
                  { value:15,
                    format:2,
                    id:Math.random(),
                  },
      ]
    }
  },
  methods:{
     add(){
       let newCounter={
          value: this.value,
          format: this.format,
          id:Math.random(),
      }
      this.counters.push(newCounter);
    },
    deleteMe(){
          if(this.counters.length>3){
            this.counters.pop();
          }
    },
  },
  computed:{

  },
  components:{
    'counter':Counter,
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

body{
    background-color: #E08548;
}

.list-item {

}
.list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active for <2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}

</style>
