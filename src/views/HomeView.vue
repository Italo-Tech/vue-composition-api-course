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
<script>
export default {
  data() {
    return {
      counter: 0
    }
  },
  watch: {
    count(newCount, oldCount) {
      if(newCount == 10) alert('Number Ten')
    }
  },
  methods: {
    increment() {
      this.counter++
    },
    decrement() {
      this.counter--
    }
  },
}
</script>

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
/* IMPORTS */
import { reactive, computed, watch, onMounted, onBeforeMount, onUpdated, onUnmounted, onBeforeUpdate, onBeforeUnmount, onActivated, onDeactivated } from "vue";

/* APP TITLE */
const appTitle = 'My Amazing Counter App'
const counterData = reactive({
  count: 0,
  title: 'My Counter'
})

/* COUNTER */
/*Computed*/
const evenOrOdd = computed(() => {
  if(counterData.count == 0) return 'neutro'
  else if(counterData.count % 2 === 0) return 'par';
  return 'ímpar'
})
/*Watch*/
watch(() => counterData.count, (newCount, oldCount) => {
  if(newCount == 20) return alert('Way to go! You mande it to 20!!')
  console.log(newCount, oldCount)
})

const increment = (amount, event) => {
  console.log(event)
  counterData.count += amount
}
const decrement = (amount, event) => {
  console.log(event)
  counterData.count--
}

/* LIFECYCLE HOOKS */
/*Chamado após a montagem do componente*/
onMounted(() => {
  console.log('onMounted -> Após o componente ser montado')
})
/*Chama apos o DOM mudar de estado*/
onUpdated(() => {
  console.log('onUpdated -> Após o componente atualizar')
})
/*Chamado após a desmontagem do componente*/
onUnmounted(() => {
  console.log('onUnmounted -> Após a desmontagem do componente')
})
/*Chamado antes do componente ser montado*/
onBeforeMount(() => {
  console.log('onBeforeMount -> Antes do componente ser montado')
})
/*Chamado antes que o componente atualize o DOM*/
onBeforeUpdate(() => {
  console.log('onBeforeUpdate -> Antes de Atualizar o DOM')
})
/*Chamados antes do componente ser desmontado*/
onBeforeUnmount(() => {
  console.log('onBeforeUnmount -> Antes do componente ser demonstado')
})
/*Ativa após o componente ser inserido no DOM*/
onActivated(() => {
  console.log('onActivated -> Ativa após o componente ser inserido no DOM')
})
/*Desativa após o componente ser REMOVIDO do DOM*/
onDeactivated(() => {
  console.log('onDeactivated -> Desativa após o componente ser removido do DOM')
})
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
