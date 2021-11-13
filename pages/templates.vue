<template>
  <div class="row">
   <iotbutton :config="configButton"></iotbutton>
   <iotindicator :config="configIndicator"></iotindicator>
   <!-- <button @click="sendData1()">SEND</button> -->
   <base-button  @click="sendData1()" type="danger" class="mb-3 pull-right" size="lg">SEND</base-button>
  

  </div>
 </template>

 <script>

 export default {
  
   data(){
     return {
       value:false,

      configButton:{
        userId: "userid",
        selectedDevice: {
          name: "Home",
          dId: "8888",
          templateName: "Power Sensor",
          templateId: "984237562348756ldksjfh",
          saverRule: false
        },
        variableFullName: "Pump",
        variable: "var1",
        icon: "fa-sun",
        column: "col-6",
        widget: "indicator",
        class: "success",   
        message: "{'fanstatus': 'stop'}"
      },
      configIndicator: {
        userId: "userid",
        selectedDevice: {
          name: "Home",
          dId: "8888",
          templateName: "Power Sensor",
          templateId: "984237562348756ldksjfh",
          saverRule: false
        },
        variableFullName: "Pump",
        variable: "var1",
        icon: "fa-sun",
        column: "col-6",
        widget: "indicator",
        class: "success"
      },        
    };
  },
    methods: {
     sendData1() {
      this.value = !this.value;
      const toSend = {
        value: this.value
      };
      this.$nuxt.$emit("userid/8888/var1/sdata", toSend);
    },      

    }
   
 };
 </script>