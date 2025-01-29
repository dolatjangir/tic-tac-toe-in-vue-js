<!--
 event :- event are a way to handle the interactions between the user and the application
 like:- click,key presses,form submitting nd many more.

 Emit----
 The $emit method is called on the component instance (e.g., this.$emit or $emit in templates).
It triggers an event with a specified name.
You can optionally pass data as additional arguments to the event.


this is IncreaseButton.vue child component
<template>
  <button @click="$emit('increaseBy', 1)">
    Increase by 1
  </button>
</template>




!@#$%^&*()_)(*&^%$#@!@#$%^&*()_)(*&^%$#@#$%^&*()_(*&^%$#$%^&*()*& ^%$#@#$%^&*(*&^%$#@)))_________--------------___________--
this is App.vue parent component
<template>
  <div>
    <h1>Counter: {{ counter }}</h1>
    <IncreaseButton @increaseBy="handleIncrease" />
  </div>
</template>

<script>
import IncreaseButton from './IncreaseButton.vue';

export default {
  components: {
    IncreaseButton
  },
  data() {
    return {
      counter: 0
    };
  },
  methods: {
    handleIncrease(value) {
      this.counter += value; // Increment counter by the value emitted
    }
  }
};
</script>

  -->