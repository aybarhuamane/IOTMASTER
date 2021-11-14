<template>
  <div>
    
    <!-- FROM ADD DEVICES -->
    <div class="row">
      <card>
        <div slot="header">
          <h4 class="card-title"> Add new device    </h4>
        </div>

        <div class="row"> 
          
          <div class="col-4">
            <base-input label="Device Name" type="text" placeholder="Ex: Home: office..">  </base-input>            
          </div>

          <div class="col-4">
            <base-input label="Device Name" type="text" placeholder="Ex: Home: office..">  </base-input> 
          </div>             

          <div class="col-4">
            <slot name="label">
              <label> Template </label>
            </slot>


            <el-select value="1" placeholder="Select Template">
              <el-option
              class="text-dark"
              value="Template 1"
              label="Template 1"
              ></el-option>

              <el-option
              class="text-dark"
              value="Template 2"
              label="Template 2"
              ></el-option>

              <el-option
              class="text-dark"
              value="Template 3"
              label="Template 3"
              ></el-option>              
            </el-select>

          </div>
        </div>

        <div class="row pull-right">
          <div class="col-12">
            <base-button type="green" class="nb-3" size ="lg">Add </base-button>

          </div>
        </div>

      </card>
    </div>

  <!-- DEVICES TABLE -->   
    <div class="row">
      <card>
        <div slot="header">
          <h4 class="card-title"> Add new device    </h4>
        </div>

        <el-table :data="devices">

          <el-table-column label="#" min-width ="50" align="center">
            <div slot-scope="{ row, $index }">
              {{$index +1}}
            </div>

          </el-table-column>

          <el-table-column prop="name" label="Name"></el-table-column>

          <el-table-column prop="dId" label="Device Id"></el-table-column>

          <el-table-column prop="templateName" label="Template"></el-table-column>
          
          <el-table-column  label="Actions">
            <div slot-scope="{ row, $index }">
                {{row.saverRule}}
            <el-tooltip content="Database Saver">
                <base-switch @click="updateSaverRuleStatus($index)" :value="row.saverRule" type="danger" on-text="On" off-text="Off"></base-switch>
            </el-tooltip>
              <el-tooltip content="Delete" effect="light" :open-delay="300" placement="top">
                <base-button type="danger" icon size="sm" class="btn-link" @click="deleteDevice(row)">
                  <i class="tim-icons icon-simple-remove"></i>
                </base-button>  

              </el-tooltip>

            </div>

            <el-tooltip content="Delete" effect="light" :open-delay="300" placement="top">
              <base-button type="danger" icon size="sm" class="btn-link" @click="deleteDevice(dI)">
                <i class="tim-icons icon-simple-remove"></i>
              </base-button>  

            </el-tooltip>



          </el-table-column>
        

        </el-table>

      </card>
    </div>

  <Json :value="devices"></Json>
  </div>

</template>

<script>
import { Table, TableColumn} from "element-ui";
import {Select, Option} from "element-ui";

export default{
  components:{
    [Table.name]: Table,
    [TableColumn.name]: TableColumn ,
    [Option.name]: Option,
    [Select.name]: Select,
  },
  data(){
    return {
      devices: [
        {
          name: "home",
          dId: "888",
          templateName:"power Sensor",
          templateId: "99912312414124",
          saverRule: false
        },
        {
          name: "office",
          dId: "83",
          templateName:"power Sensor",
          templateId: "99912312414124",
          saverRule: true
        },
        {
          name: "erick",
          dId: "888",
          templateName:"power Sensor",
          templateId: "999122312414124",
          saverRule: false
        }              
      
      ]
    };
  },
  methods:{
    deleteDevice(device){
     alert("DELETING " + device.name);   

    },
    updateSaverRuleStatus(index){
      
      this.devices[index].saverRule = !this.devices[index].saverRule;
    }
  }
};
</script>