<template>
  <div class="home">
    <div>

      <h2>{{ appTitle }}</h2>
      <h3>{{ counterData.title }}:</h3>

      <button @click.prevent="decrement" class="btn">-</button>
      <span class="counter">{{ counterData.count }}</span>
      <button @click.prevent="increment" class="btn">+</button>
    </div>

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
import { reactive } from "vue";

// const counter = ref(0),
//     counterTitle = ref('My Counter')
const appTitle = 'My Amazing Counter App'

const counterData = reactive({
  count: 0,
  title: 'My Counter'
})

const increment = () => {
  counterData.count++
}
const decrement = () => {
  counterData.count--
}

</script>

<style>
.home {
  text-align: center;
  padding: 20px;
}
.btn, .counter {
  padding: 5px 10px;
  font-size: 20px;
}
.edit {
  margin-top: 60px;
}
</style>
