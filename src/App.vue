<template>
  <div id="app" class="h-screen flex items-center justify-center flex-col gap-6">
    <CounterComponent :initialCount="0" :initialMin="0" :initialMax="10" :initialValue="1" />
  </div>
</template>

<script>
import CounterComponent from './components/CounterComponent.vue';

export default {
  components: {
    CounterComponent
  }
};
</script>
