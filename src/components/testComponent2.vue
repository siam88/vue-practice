<template>
  <div>
        <h1>hello Bangladesh</h1>
        <p>{{txt}}</p>
  </div>
</template>

<script>
export default {
    name:'test2',
    props:{
        txt:{
            type:String,
            required:true
        }
    },
    methods: {
         
    },
}
</script>
<style scoped>
h1{
    color: blueviolet;
}
p{
    color:blue ;
}
</style>