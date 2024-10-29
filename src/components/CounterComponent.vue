<template>
  <div id="Counter" class="h-screen flex items-center justify-center flex-col gap-6">
    <div id="button" class="flex items-center justify-center flex-row gap-6">
      <p>Mínimo</p>
      <div id="min">
        <input 
        type="number" 
        class="m-2 w-10 border-2 border-black" 
        v-model.number="min" 
        @input="adjust"
        >
        <button 
        :disabled="count <= min" 
        class="disabled:cursor-not-allowed disabled:opacity-70 border-2 border-black bg-green-600 p-5 w-16 rounded-md hover:opacity-90 transition-all" 
        @click="decrement">-</button>
      </div>
      <h1 class="text-2xl">Valor: {{ count }}</h1>
      <div id="max">
        <button 
        :disabled="count >= max || min > max" 
        class="disabled:cursor-not-allowed disabled:opacity-70 border-2 border-black bg-green-600 p-5 w-16 rounded-md hover:opacity-90 transition-all" 
        @click="increment">+</button>
        <input
        type="number" 
        class="m-2 w-10 border-2 border-black" 
        v-model.number="max"
        @input="adjust"
        >
      </div>
      <p>Máximo</p>
    </div>
    <input type="number" placeholder="Add value..." class="m-2 w-16 border-2 border-black" v-model.number="value">
  </div>
</template>

<script>
export default {
  name: "CounterComponent",
	props: {
    initialCount: {
      type: Number,
      default: 0
    },
    initialMin: {
      type: Number,
      default: 0
    },
    initialMax: {
      type: Number,
      default: 10
    },
    initialValue: {
      type: Number,
      default: 1
    }
  },
  data() {
    return {
      count: this.initialCount,
      value: this.initialValue,
      max: this.initialMax,
      min: this.initialMin
    };
  },
	methods: {
		increment() {
			if (this.count < this.max) {
				this.count += this.value;
				if (this.count > this.max) {
					this.count = this.max;
				}
			}
		},
		decrement() {
			if (this.count > this.min) {
				this.count -= this.value;
				if (this.count < this.min) {
					this.count = this.min;
				}
			}
		},
    adjust(){
      if(this.count < this.min){
        this.min = this.count;
      }
      if(this.count > this.max){
        this.max = this.count
      }
    }
	},
};
</script>