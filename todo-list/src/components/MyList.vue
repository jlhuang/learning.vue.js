<template>
  <div>
      <ul>
        <MyItem v-for="todo in todos" :key="todo.id" :todo="todo"/>
      </ul>
  </div>
</template>

<script>
import MyItem from "./MyItem"
export default {
    name: 'MyList',
    props:['todos'],
    components: {MyItem}
}
</script>

<style>

</style>