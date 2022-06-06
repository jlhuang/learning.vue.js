<template>
  <div>
      <li>
        <input type="checkbox" :checked="todo.checked" @change="handleChange(todo.id)"/>
        {{todo.name}}
        <button class="btn" @click="handleDelete(todo.id)">delete</button>
      </li>
  </div>
</template>

<script>

export default {
    name: 'MyItem',
    props: ['todo'],
    methods: {
        handleChange(id) {
            this.$bus.$emit('checkTodo',id)
        },
        handleDelete(id) {
            if(confirm('Do you really want to delete?')) {
                this.$bus.$emit('deleteTodo',id)
            }
        }
    },
}
</script>

<style>
.btn {
    display: none;
}
li:hover{
    background-color:aqua;
}
li:hover button{
    display:inline;
}
</style>