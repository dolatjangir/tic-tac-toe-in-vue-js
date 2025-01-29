<template>
  <div>
    <!-- v-html -->
     <div class="" v-html="htmlContent"></div>
     <!-- v-bind -->
      <div class="" v-bind="bindex"></div>
  </div>
</template>
<script>
export default{
  data(){
    return{
      // for v-html
      htmlContent : "<p>hello from v-html</p>"
  
    }
  },
  methods :{
   
    }
}
</script>