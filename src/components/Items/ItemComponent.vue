<template>
   <div>
      <h2>Item List</h2>
   </div>
    <!-- Show items -->
     <ul v-for="data in Items" :key="data.id">
        <li>{{ data.name }} - <input type="checkbox" v-model="data.completed" @click="completedItems(data.id)"/></li>
     </ul>
     <!-- {{ Items }} -->
</template>
<script setup lang="ts">
import type { ItemInterface } from '@/Models/Items/Item.interface';
defineProps<{Items: ItemInterface[] }>();

const emit=defineEmits<{(e:"changeItem",id:number):any}>(); 
const completedItems=(id)=>{
   emit('changeItem',id);
}
</script>