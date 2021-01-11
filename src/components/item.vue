<template>
    <div class="item" @click="favourite(item)">
       <div class="user-profile_item">
          <div>
            @{{username}}
          </div>
          <div>
            <div class="item-content">
               {{item.content}}  || {{item.selectedItemType}}
            </div>
          </div>
       </div>
    </div>
</template>

<script>
export default {
    name:'Item',
    props:{
        username:{
            type:String,
            required:true
        },
         item:{
            type:Object,
            required:true
        }
    },
    methods:{
        favourite(item){
            console.log(item);
            this.$emit('favourite',item);
        }
    }
}
</script>

<style scoped>  
.item{
    padding: 20px;
    background-color: beige;
    border-radius: 5px;
    border: 1px solid #DFE3E8;
    box-sizing: border-box;
    transition: all 0.25s ease;

}
.item:hover{
    transform: scale(0.9,0.9);
}
.item_user{
    font-weight: bold;
}
</style>