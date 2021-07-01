<template>
  <v-app>
    <v-card>
    <div v-for="(data, i) in dataUser" :key="i">         
    <v-row>
      <v-col>
        <p>{{data.phone}}</p>
      </v-col>
      <v-col>
        <p>{{data.city}}</p>
      </v-col>
       <v-col>
        <p>{{data.name}}</p>
      </v-col>
       <v-col>
        <p>{{data.website}}</p>
      </v-col>
       <v-col>
        <p>{{data.email}}</p>
      </v-col>
       <v-col>
        <p>{{data.username}}</p>
      </v-col>
      <v-col>
        <p>{{data.address.city}}</p>
      </v-col>
        <v-col>
        <p>{{data.company.name}}</p>
      </v-col>
    </v-row>
    </div>
    </v-card>
    <v-card class="mt-5">
      <div  v-for="(data, i) in dataFoto" :key="i">
        <v-row>
          <v-card>
             <v-img
              :src="data.url"
              class="white--text align-end"
              
              height="200px"
            >
              <v-card-title v-text="data.title"></v-card-title>
            </v-img>
          </v-card>
        </v-row>
      </div>
    </v-card>
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
import axios from 'axios';
export default {
  name: 'App',

  data: () => ({
    dataUser:[],
    dataFoto:[]
  }),
   mounted(){
     console.log("mount");
     this.getUser()
     this.getfoto()
   },
   methods:{
     getUser(){
     axios.get('https://jsonplaceholder.typicode.com/users')
     .then((res)=> {console.log(res)
     this.dataUser = res.data
     console.log(this.dataUser);
     })
     .catch((err)=> console.log(err))
     },
     getfoto(){
       axios.get('https://jsonplaceholder.typicode.com/albums/1/photos')
       .then((res) => {console.log(res)
       this.dataFoto = res.data
       console.log(this.dataFoto);
       })
       .catch((err)=> console.log(err))
     }
   }
};
</script>
