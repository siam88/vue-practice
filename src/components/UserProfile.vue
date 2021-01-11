<template>
    <div class="user-profile">
        <div class="user-profile_user-panel">
            <h1>@{{user.username}}</h1>
            <div class="user-profile_admin-badge" v-if="user.isAdmin">
                Admin
            </div>
            <div class="user-profile_admin-badge" v-else>
                Not admin
            </div>
            <div class="user-profile_user-panel">
                <strong>Followers:</strong> {{followers}}
                <button @click="followUser">
                    follow
                </button>
                <button @click="makeAdmin" v-if="!user.isAdmin">make admin </button>
                <button @click="makeAdmin" v-else>remove admin </button>
            </div>
            <div class="user-profile__list_wrapper" @submit.prevent="createNewItem">
                <!-- <div class="user-profile__list-item" v-for="(item) in user.list" :key="item.id">
                    {{item.content}}
                </div> -->

                <item v-for="item in user.list" :key="item.if" :username="user.username" :item="item" @favourite="toggleFavourite" />
            </div>

             <div class="user-profile_create_item">
                <label for="newItem"><strong> Item</strong></label>
                <textarea class="newitem" rows="4" v-model="itemContent"/>
            </div>
            <form class="user-profile_create_item" @submit.prevent="createNewItem">
                <div class="user-profile_create_item_type">
                    <label for="newItemType"><strong> Type :</strong></label>
                    <select id="newitemType" v-model="selectedItemType">
                        <option :value="option.value" v-for="(option,index) in itemType" :key="index">
                            {{ option.name}}
                        </option>
                    </select>
                </div>
                <button>
                    Item
                </button>
            </form>
        </div>
        <div class="user-profile_user-panel">
            <h1>favourites</h1>
             <div class="user-profile__list_wrapper">
               

                <div 
                    
                    v-for="item in favourite" :key="item.id">
                      <button style=" background-color:red"  @click="deleteItem(item.id)">x</button> <a   >{{item.content}}</a> 
                    </div>
            </div>
        </div>

       
    </div>
    
</template>

<script>
import Item from './item.vue';
export default {
    name:'User',
    selectedItemType:"draft",
    itemContent:"",
    components:{Item},
    data(){
        return{
            itemType:[
                {value:'draft',name:'Draft'},
                {value:'instant',name:'Instant Item'}

            ],
            followers:0,
            favourite:[],
            user:{
                id:1,
                username:'_SIAM',
                firstName:'Rafshanul Hoque',
                lastName:'Siam',
                email:'rafshanulsiam811@gmail.com',
                isAdmin:false,
                list:[
                    {id:1,content:"THIS IS AMAZING 1",selectedItemType:"draft"},
                    {id:2,content:"THIS IS AMAZING 2",selectedItemType:"draft"}

                ]
            }
        }   
    },
     computed:{
        fullName(){
            return `${this.user.firstName} ${this.user.lastName}` ;
        },
    },
    watch: {
       followers(newFollowerCount,oldFollowerCount){
           if(newFollowerCount>oldFollowerCount){
            console.log(`${this.user.username} has gained a new followers`)
           }
       }
    },
  methods:{
      followUser(){
          this.followers+=1
      },
      makeAdmin(){
          this.user.isAdmin=!this.user.isAdmin
      },
      toggleFavourite(item){
          this.favourite.push(item);
          console.log(`Favourite item #${item.content}`);
      },
      deleteItem:function(id){
            console.log(` item #${id}`);
      },
      createNewItem(){
        
          if(this.itemContent && this.selectedItemType !=='draft'){
              this.user.list.unshift( {
                  id:this.user.list.length+1,
                  content:this.itemContent,
                  selectedItemType:this.selectedItemType
              })
              this.itemContent=""
          }
      }
  },
  mounted() {
      this.followUser();
  },
}
</script>

<style >
    .user-profile{
        display: grid;
        grid-template-columns: 1fr 3fr;
        width: 100%;
        padding: 50px 5%;
        text-align: center;
    }

    .user-profile_user-panel{
        display: flex;
        flex-direction:column ;
        margin-right: 50px;
        padding: 20px;
        background-color:white ;
        border-radius:5px;
        border:1px solid #DFE3E8;
        }
    .user-profile_admin-badge{
        background: rebeccapurple;
        color: white;
        border-radius: 5px;
        margin-right:auto ;
        padding: 0 10px;
        font-weight: bold;
       
    }
    h1{
        margin: 0;
        
    }
    .user-profile_create_item{
        display: flex;
        flex-direction: column;
        border-top: 1px solid black;
        padding-top:20px ;
        
    }
</style>