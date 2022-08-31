<template>
    <div>
        <ul>
            <h1>Film</h1>
            <li v-for="(filmSelez, index) in filmList" :key="index">
                {{filmSelez.title}}-
                {{filmSelez.original_title}}-
                {{filmSelez.original_language}}-
                {{filmSelez.vote_average}}
                <img :src="'http://image.tmdb.org/t/p/w342/' + filmSelez.backdrop_path" alt=""/>
            </li>
            
        </ul>

        <ul>
            <h1>SerieTv</h1>
            <li v-for="(serieSelez, index) in serieTv" :key="index">
                {{serieSelez.name}}-
                {{serieSelez.original_name}}-
                {{serieSelez.original_language}}-
                {{serieSelez.vote_average}}
                <img :src="'http://image.tmdb.org/t/p/w342/' + serieSelez.backdrop_path" alt=""/>
            </li>
        </ul>
    </div> 
  
</template>

<script>
export default {
    name:'MyMain',
    data(){
        return{
            urlCopertina:'https://image.tmdb.org/t/p/'
        }
    },

   
    props:{
        filmList:Array,
        serieTv: Array
    }
}
</script>

<style lang="scss">

</style>
