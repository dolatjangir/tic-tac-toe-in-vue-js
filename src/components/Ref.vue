<template>
    <p @click="incriment">{{ count }}</p>
</template>
<!-- ref() take a argument and returns it wrapped within a ref object with a .value property -->
<!-- <script setup>
import {ref} from 'vue'
const count = ref(0);
console.log(count)
console.log(count.value)
count.value++

</script> -->

<!-- //////===========++++++++++++++++++++++++++__________________-------------------__???????????????????????????????????? -->

<!-- to access refs in a components templete ,declare and return them from a components setup() function  -->
 <!--when use this setup function then we dont need this .value property   
 Notice that we did not need to append .value when using the ref in the template. For convenience, refs are automatically unwrapped when used inside templates -->
<!-- like that --> 
 <script >
import {ref} from 'vue'
export default{
    setup(){
        const count = ref(0);
        function incriment(){
            count.value++
        } return{
            count,
            incriment
        }
       
    }
    
}
</script>