<template>
  <div>
   
   <iotindicator></iotindicator>
   <!-- <button  >SEND</button> -->
    <base-button  @click="sendData" type="success" class="nb-3" size ="lg">Add </base-button>

  </div>
 </template>

 <script>
  
 export default {
   data(){
     return {
       value:false
     }
   },
    methods: {
      sendData(){
        this.value = !this.value;
        const toSend={
          value: this.value
        }
        this.$nuxt.$emit('widget-topic', toSend );
      }
    }
   
 }
 </script>