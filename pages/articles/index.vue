<template>
    <section style="display:flex; flex-flow: row wrap;justify-content: center">
        <ArticleThumb  
            v-for="article in articles" 
            :key="article.id"
            :id="article.id"
            :title="article.title"
            :thumbnails="article.thumbnail_images"
            :date="article.date"
            />
    </section>
</template>

<script>

import ArticleThumb from "@/components/ArticleThumb";
const axios = require('axios');

export default {
    components:{
        ArticleThumb
    },

    data: ()=> {
        return {
            articles:'lknjk',
        }
    },

    beforeCreate () {

        

        axios.get('http://femme.nextmedia.ma/api/get_recent_posts')
            .then((response)=> {
                // handle success
                this.articles= response.data.posts; 
                console.log(this.articles[0].thumbnail_images.thumbnail.url);
                               
            })
            .catch( (error) => {
                // handle error
                console.log(error);
            });

    }
    
}
</script>

