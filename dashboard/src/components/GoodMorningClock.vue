<script>
import { ref } from 'vue';
import { onMounted } from 'vue';
import { onUnmounted } from 'vue';
    export default
    {
        setup(){
            const tralala = ref(0)
            const setValue = () => {
                if(tralala.value == 'yolo')
                    tralala.value = 'miau'
                else
                    tralala.value = 'yolo'
            }

            const currentTime = ref(new Date().toLocaleTimeString());
            const updateTime = () => {
                currentTime.value = new Date().toLocaleTimeString()
            }
            
            let intervalId
            onMounted(()=> {
                intervalId = setInterval(updateTime, 1000)
            });

            onUnmounted(() => {
                clearInterval(intervalId);
            });

            return {
                currentTime, tralala,setValue
            }
        }
    }
</script>

<template>
    <h1>Time: {{currentTime}}</h1>
    <h2>{{tralala}}</h2>
    <button @click=setValue>clickkkk</button>
</template>
