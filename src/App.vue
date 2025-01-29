

<template>
<div>
    <h1>My Todo</h1>
    <h3>{{ completedAll }}</h3>
</div>
<!-- Show list -->
 <!-- Prop data to child component -->
<ItemList :Items="DataItemList" @changeItem="completedItem"></ItemList>
</template>

<script setup lang="ts">

import type { ItemInterface } from "./Models/Items/Item.interface";
//import item list Component 
import ItemList from "./components/Items/ItemComponent.vue"

import { computed, reactive} from "vue";
//create data item
const DataItemList: ItemInterface=reactive([
{
    id:1,
    name:'coffee',
    completed:true,
},
{
    id:2,
    name:'Books',
    completed:false,
},
{
    id:5,
    name:'Pen',
    completed:false,
},
{
    id:4,
    name:'Laptop',
    completed:false,
},
]);
const completedItem=(id)=>{
   // alert('id+item'+  id);
};
const completedAll=computed(()=>{
    const all=DataItemList.length;
    let countCompleted=0;

    DataItemList.forEach(element => {
        if(element.completed){
            countCompleted++;
        }
        
    });
    return countCompleted==all?'[all Todo is Completed]':'[No]';
});

</script>
