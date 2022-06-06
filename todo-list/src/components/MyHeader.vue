<template>
  <div>
      <input type="text" v-model="title" @keyup.enter="add">
  </div>
</template>

<script>
import {nanoid} from 'nanoid'
export default {
    name: 'MyHeader',
    data() {
        return {
            title:''
        }
    },
    methods: {
        add() {
            if(this.title.trim() ==='') {
                alert('please input the todo corectly')
                return
                }

            const todoObj = {
                id:nanoid(),
                name:this.title,
                checked:false
            }
            this.title=''
            this.$emit('addTodo',todoObj)
        }
    }
}
</script>

<style>

</style>