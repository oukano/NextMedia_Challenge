<template>

    <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <nuxt-link :to="'/articles'" class="navbar-brand" href="#">الرئيسية</nuxt-link>
    <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
        <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
        <ul class="navbar-nav">
        
        <li class="nav-item" v-for="menu in navBarMenu" :key="menu.id">
            <nuxt-link :to="'/categorie/'+menu.object_id "  class="nav-link" >{{menu.label}}</nuxt-link>
        </li>
        </ul>
        
    </div>
    </nav>

</template>

<script>

const axios = require('axios');
export default {

    
    data: ()=> {
        return {
            navBarMenu:'',
        }
    },
    
    created () {

        

        axios.get('http://femme.nextmedia.ma/api/menus/get_menu/?menu_id=7')
            .then((response)=> {
                // handle success
                this.navBarMenu= response.data.menu.output; 
                // console.log(this.navBarMenu);
                               
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            });

    }
    
}
</script>

<style scoped>


</style>
