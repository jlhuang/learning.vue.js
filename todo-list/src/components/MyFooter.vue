<template>
  <div  v-show="todos.length">
      <input type="checkbox" v-model="isCheckedAll"/>
      <!--<span>selected/all:{{todos.filter(todo=>todo.checked===true).length}}/{{todos.length}}</span>-->
      <span>selected/all:{{checkedTotal}}/{{isAll}}</span>
      <button @click="deleteChecked">delete all done</button>
  </div>
</template>

<script>

export default {
    name: 'MyFooter',
    props:['todos','checkAll','deleteDone'],
    computed: {
        checkedTotal() {
            return this.todos.reduce((pre, todo)=> pre + (todo.checked?1:0),0)
        },
        isAll() {
            return this.todos.length
        },
        isCheckedAll: {
            get() {
                return this.isAll === this.checkedTotal
            },
            set(value) {
                this.checkAll(value)
            }
        }
    },
    methods:{
        deleteChecked() {
            this.deleteDone()
        }
    }
}
</script>

<style>

</style>