<template>
    
    <nuxt-link :to="'/article/'+id" >
        <section>
            <div class="card" style="width: 18rem;">
                <img class="card-img-top"  alt="Card image cap">
                <div class="card-body">
                    <h5 class="card-title">{{title}}</h5>
                    <span > {{date}} ----- {{catid}} </span>
                </div>
            </div>
        </section>
    </nuxt-link>

    
</template>

<script>
export default {

    props: ["id","title","catid","thumbnails","date"],
    
    
     
}
</script>
