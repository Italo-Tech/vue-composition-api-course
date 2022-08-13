<template>
  <div class="home">
    <div>

      <h2>{{ appTitle }}</h2>
      <h3>{{ counterData.title }}:</h3>

      <button @click.prevent="decrement(1, $event)" class="btn">--</button>
      <button @click.prevent="decrement(2, $event)" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click.prevent="increment(1, $event)" class="btn">+</button>
      <button @click.prevent="increment(2, $event)" class="btn">++</button>
    </div>

    <p>This number is {{ evenOrOdd }}</p>

    <div class="edit">
      <h4>Edit counter title:</h4>
      <input v-model="counterData.title" type="text">
    </div>
  </div>
</template>

<!--Option API-->
<!--<script>
export default {
  data() {
    return {
      counter: 0
    }
  },
  methods: {
    increment() {
      this.counter++
    },
    decrement() {
      this.counter&#45;&#45;
    }
  }
}
</script>-->

<!--Composition API-->
<!--<script>
import {ref} from "vue";

export default {
  setup() {
    const counter = ref(0)
    const increment = () => { counter.value++ }
    const decrement = () => { counter.value&#45;&#45; }

    return {
      counter,
      increment,
      decrement
    }
  }
}
</script>-->

<!--SFC <script setup>-->
<script setup>
import { reactive, computed } from "vue";

const appTitle = 'My Amazing Counter App'

const counterData = reactive({
  count: 0,
  title: 'My Counter'
})
/*Computed*/
const evenOrOdd = computed(() => {
  if(counterData.count == 0) return 'neutro'
  else if(counterData.count % 2 === 0) return 'par';
  return 'ímpar'
})

const increment = (amount, event) => {
  console.log(event)
  counterData.count += amount
}
const decrement = (amount, event) => {
  console.log(event)
  counterData.count--
}

</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn, .counter {
  margin: 0 5px;
  padding: 5px 10px;
  font-size: 20px;
}
.edit {
  margin-top: 60px;
}
</style>
