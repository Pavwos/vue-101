<template>
  <div id="app" class="h-screen flex items-center justify-center flex-col gap-6">
    <div id="button" class="flex items-center justify-center flex-row gap-6">
      <button :disabled="count <= 0" class="disabled:cursor-not-allowed disabled:opacity-70 bg-green-600 p-5 w-16" @click="decrement">-</button>
      <h1 class="text-2xl">Valor: {{ count }}</h1>
      <button :disabled="count >= 10" class="disabled:cursor-not-allowed disabled:opacity-70 bg-green-600 p-5 w-16" @click="increment">+</button>
    </div>
    <input type="number" placeholder="Add value..." class="outline-none border-b-neutral-800" v-model.number.lazy="value">
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