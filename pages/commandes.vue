<template>
<div>
 <Navbar/>
    <div class="container">
        <h1 class="display-1">
           test
           <Test/>
        </h1>
     <ul id="example-1">
  <li v-for="produit in produits" :key="produit.name">
    {{ produit.name }}   {{produit.price}}
  </li>
</ul>
         <Produit  v-for="produit in produits"
  v-bind:price="produit.price"
   v-bind:name="produit.name"
  v-bind:key="produit.name"/>
    </div>
</div>
</template>

<script>
/* import Produit from '@/components/Produit.vue' */
export default {
    
  data(){
      return {
        produits:[{
            name: 'pizza', price: 2.00
        },{
            name: 'choux', price: 3.00
        }]
      }
  },

async mounted() {
  this.getIncidents ();
},
methods:{
  async getIncidents(){
    const ip = await this.$axios.$get('http://localhost:3001/api/users')
    this.ip = ip
    console.log(ip)
  }
}


}

</script>

<style scopted>

</style>