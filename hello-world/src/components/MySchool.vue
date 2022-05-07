<template>
    <div class="demo">
        <h2>学校名字：{{schoolName}}</h2>
        <h2>学校地址：{{schoolAddress}}</h2>
        <button @click="showName">点我显示名字</button>
    </div>
</template>

<script>
export default {
    name: 'MySchool',
    data() {
        return {
            schoolName: '复旦大学',
            schoolAddress: '上海杨浦区'
        }
    },
    methods: {
      showName() {
          alert(this.schoolName)
      }  
    },
}
</script>

<style>
.demo {
    background-color:aquamarine
}

</style>
