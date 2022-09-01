<template>
    <div>
        <ul>
            <h1>Film</h1> 
            <li v-for="(filmSelez, index) in filmList" :key="index">
                {{filmSelez.title}}-
                {{filmSelez.original_title}}-
                <img :src=urlBandiera alt=""/>{{bandiera(filmSelez.original_language)}}
                {{voto(filmSelez.vote_average)}}
                <img :src="'http://image.tmdb.org/t/p/w342/' + filmSelez.poster_path" alt=""/>
            </li>
            
        </ul>

        <ul>
            <h1>SerieTv</h1>
            <li v-for="(serieSelez, index) in serieTv" :key="index">
                {{serieSelez.name}}-
                {{serieSelez.original_name}}-
                <img :src="urlBandiera" alt=""/>{{bandiera(serieSelez.original_language)}}-
                {{voto(serieSelez.vote_average)}}
                <img :src="'http://image.tmdb.org/t/p/w342/' + serieSelez.poster_path" alt=""/>
            </li>
        </ul>
    </div> 
  
</template>

<script>


export default {
    name:'MyMain',
    data(){
        return{
            urlCopertina:'https://image.tmdb.org/t/p/',
            urlBandiera:""
        }
    },
    methods:{
       voto(voto){
            let voti= voto /2;
            let votoTo5=voti.toFixed();
            return votoTo5
        },
        bandiera(lingua){
            let bandiera=lingua;
            if(bandiera=='en'){
                bandiera='gb'
            }if(bandiera=="zh"){
                bandiera="cn"

            }if(bandiera=="ja"){
                bandiera="jp"
            }
            let flag= 'https://flagcdn.com/16x12/'+ bandiera +'.png';
           
            this.urlBandiera=flag
            
        }

    },
    
   
    props:{
        filmList:Array,
        serieTv: Array
    }
}
</script>

<style lang="scss">
@import '~@fortawesome/fontawesome-free/css/all.css';

</style>
