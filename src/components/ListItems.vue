<template>
  
  <div>
      <ol class="list-group list-group-numbered">
      <div v-for="item in Items" :key="item.id">
          <ListItem :item="item" />
      </div>
      </ol>
  </div>

</template>

<script>
import ListItem from './ListItem.vue'
export default {
name:'ListItems',
props:{
    Items: Array,
},
components:{
    ListItem,
}
}
</script>

<style>

</style>