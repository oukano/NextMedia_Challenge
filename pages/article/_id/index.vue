<template dir="rtl" >
    <section dir="rtl">
        <img  :src="img" alt="">
        <h1>{{poste.title}}</h1>
        <div v-html="poste.content"></div>
    </section>
</template>

<script>
const axios = require('axios');

export default {
    
    data : () => {
        return {
            poste:'',
            img:''
        }
    },

     beforeCreate () {


        axios.get('http://femme.nextmedia.ma/api/get_post/?id='+this.$route.params.id)
            .then((response)=> {
                // handle success
                this.poste= response.data.post; 
                this.img= this.poste.thumbnail_images.large.url
                
                
                               
            })
            .catch( (error) => {
                // handle error
                console.log(error);
            });

    }
}
</script>

<style>
*{
    direction: rtl;
}
html
{
  direction: rtl;
}
</style>


