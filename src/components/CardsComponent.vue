
<template>
    <div class="col-12 col-sm-6 col-md-4 col-lg-3 bg-white">
        <div class="bg-card text-center ">
            <img class="img-fluid" :src="character.card_images[0].image_url" alt="">
            <h4>{{ character.name }}</h4>
            <p>{{ character.race }}</p>
        </div>
    </div>  
</template>

<script>
export default {
    name: 'CardsComponent',
    props: ['character']
}
</script>


<style lang="scss" scoped>
.bg-card{
    background-color:#d48f38 ;
}

</style>