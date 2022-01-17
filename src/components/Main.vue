<template>
<v-container >
    <!-- <div class="box-container">
        <input type="checkbox" name="boxes" @change="check('box_corners')">box corners<br>      
        <input type="checkbox" name="boxes"  @change="check('bounding_box')">bounding box<br>      
        <input type="checkbox" name="boxes"  @change="check('bounding_corner')">bounding corner<br>      
    </div>
   
    <ul>
        <li v-for="(value,index) in arr" :key="index">
            <div v-if="value.flag"> {{value.name}}  {{value.amount}} </div>
           
        </li>
    </ul> -->
    <v-card
    dark
    class="mx-auto"
    max-width="70%"
    tile
  > <v-toolbar dense>
       <input type="checkbox" name="boxes" @change="check('box_corners')"><v-icon>mdi-call-split</v-icon><br> 
       <v-spacer>  </v-spacer>       
        <input type="checkbox" name="boxes"  @change="check('bounding_box')"><v-icon> mdi-dialpad</v-icon><br>      
       <v-spacer>  </v-spacer>    
        <input type="checkbox" name="boxes"  @change="check('bounding_corner')"><v-icon> mdi-email</v-icon><br>      
 
    </v-toolbar>
    <v-list dense>
      <v-list-item-group
        color="primary"
      > 
      <!-- <div v-for="(value,index) in filter_arr" :key="index"></div> -->
        <v-list-item
          v-for="(item, i) in filter_arr"
          :key="i"
        >

          <v-list-item-icon>
            <v-icon  class="mt-10"  v-text="item.icon" :color="item.color" large></v-icon>
          </v-list-item-icon>
           <!-- <v-spacer>  </v-spacer> -->
          <v-list-item-content>
            <v-list-item-title v-text="item.name"></v-list-item-title>
          </v-list-item-content>
           <v-spacer>  </v-spacer>
           <v-text-field
              outlined
              v-model="item.amount"
              type="number"
              class="mt-5"
        />
        </v-list-item>
      </v-list-item-group>
     
    </v-list>
  </v-card>
</v-container>
</template>

<script>
export default {
    name:'Main',
    data: function(){
        return {
            arr : [
            {name: 'box_corners' ,  amount: '10', flag:false , icon: 'mdi-call-split', color:'yellow'},
            {name: 'box_corners' , amount: '10', flag:false, icon: 'mdi-call-split', color:'yellow'},
            {name: 'box_corners' ,  amount: '20', flag:false, icon: 'mdi-call-split', color:'yellow'},
            {name: 'box_corners' ,  amount: '30', flag:false, icon: 'mdi-call-split', color:'yellow'},
            {name: 'bounding_box' ,  amount: '40', flag:false, icon: ' mdi-dialpad', color:'green'},
            {name: 'bounding_box' , amount: '50', flag:false, icon: ' mdi-dialpad', color:'green'},
            {name: 'bounding_box' , amount: '60', flag:false, icon: ' mdi-dialpad', color:'green'},
            {name: 'bounding_box' ,  amount: '70', flag:false, icon: ' mdi-dialpad', color:'green'},
            {name: 'bounding_corner' ,  amount: '80', flag:false, icon: 'mdi-email', color:'purple'},
            {name: 'bounding_corner' ,  amount: '90', flag:false, icon: 'mdi-email', color:'purple'},
            {name: 'bounding_corner' ,  amount: '100', flag:false, icon: 'mdi-email', color:'purple'}
            ],
        }
    },
    computed:{
        filter_arr:function(){
            return this.arr.filter(i=> i.flag)
        }
    },
    methods:{
        check(val){
            for(var i=0; i<this.arr.length; i++){
                if (val == this.arr[i].name){
                    this.arr[i].flag =  !this.arr[i].flag

                }
            }
           
        }
    }
}
</script>

<style>

.v-text-field{
      width: 20px;
      height: 40%;
}
.elem{
    margin-top: 5 px;
}
</style>