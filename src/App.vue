<template>
  <h1>DC heroes</h1>
  <ul>
     <li v-for="(hero,index) in dcHeros" v-bind:key="index">{{hero.name}}</li>
  </ul>
  <!-- <input v-model.lazy="newHero"/> -->
  <form @submit.prevent="addHero">
  <input v-model="newHero" placeholder="type hero name here"/>
  <button type="submit">Add hero</button>
  </form>
</template>

<script>
export default {
    data(){
        return {

            newHero:"",
            dcHeros:[
                {name:'SuperGirl'},
                {name:'Flash'},
                {name:'Batman'},
                {name:'Arrow'},
                {name:'SuperMan'}
                ]
        }
    },
    methods:{
        addHero(){
            if (this.newHero !== ""){
                this.dcHeros.push({name: this.newHero}); this.newHero=''
            }
            
        }
    }
}
</script>

<style>

</style>