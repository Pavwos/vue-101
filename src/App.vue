<template>
  <div id="app" class="h-screen flex items-center justify-center flex-col gap-6">
    <div id="button" class="flex items-center justify-center flex-row gap-6">
      <p>Mínimo</p>
      <div id="min">
        <input type="number" class="m-2 w-10 border-2 border-black" v-model.number="min">
        <button :disabled="count <= min" class="disabled:cursor-not-allowed disabled:opacity-70 border-2 border-black bg-green-600 p-5 w-16 rounded-md hover:opacity-90 transition-all" @click="decrement">-</button>
      </div>
      <h1 class="text-2xl">Valor: {{ count }}</h1>
      <div id="max">
        <button :disabled="count >= max" class="disabled:cursor-not-allowed disabled:opacity-70 border-2 border-black bg-green-600 p-5 w-16 rounded-md hover:opacity-90 transition-all" @click="increment">+</button>
        <input type="number" class="m-2 w-10 border-2 border-black" v-model.number="max">
      </div>
      <p>Máximo</p>
    </div>
    <input type="number" placeholder="Add value..." class="m-2 w-16 border-2 border-black" v-model.number="value">
  </div>
</template>

<script>
export default {
  data(){
    return {
      count: 0,
      value: 1,
      max: 10,
      min: 0,
    };
  },
  methods:{
    increment(){
      if(this.count < this.max){
        this.count += this.value
        if(this.count > this.max){
          this.count = this.max;
        }
      } 
    },
    decrement(){
      if(this.count > this.min){
        this.count -= this.value
        if(this.count < this.min){
          this.count = this.min;
        }
      }
    },
  },  
};
</script>