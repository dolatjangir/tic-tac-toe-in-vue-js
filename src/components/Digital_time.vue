<template class="">

  <div class="flex flex-col space-y-5 items-center justify-center h-screen bg-gray-900 text-white">
    <div class="text-5xl font-bold p-6 bg-gray-800 rounded-lg shadow-lg">
      {{ currentTime }}
      
    </div>
    <div class="text-5xl font-bold p-6 bg-gray-800 rounded-lg shadow-lg">
      {{ currentDate }}
      
    </div>
  </div>

</template>
<script>
import {onMounted, onUnmounted, ref} from 'vue'
export default{
    setup(){
        const currentTime = ref("")
        const currentDate = ref("")
       
        const updateTime=()=>{
          const now = new Date();
          currentTime.value = now.toLocaleTimeString();
          currentDate.value = now.toLocaleDateString();
        }

        // set interval for update time for every second
        let timer = null;
        onMounted(()=>{
          updateTime();
          timer = setInterval(updateTime,1000);
        });
        // when kour component is destroyed the use --
        onUnmounted(()=>{
          clearInterval(timer);
        });


        return{
          currentTime,
          currentDate
        }
    }
}
</script>