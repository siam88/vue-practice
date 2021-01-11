<template>
    <h1>{{msg}}</h1>
</template>

<script>
export default {
    name:'test',
    props:{
        msg:{
            type:String,
            required:true
        }
    }
}
</script>

<style scoped>
#h1{
    color: brown;
}
</style>