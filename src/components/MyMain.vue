<template>
    <div>
        <ul>
            <h1>Film</h1> 
            <li v-for="(filmSelez, index) in filmList" :key="index">
                {{filmSelez.title}}-
                {{filmSelez.original_title}}-
                <img :src="bandiera(filmSelez.original_language)" alt=""/>
                <img :src="'http://image.tmdb.org/t/p/w185/' + filmSelez.poster_path" alt=""/>
                <div>
                    <i v-for="n in 5" :key='n' class="fa-star" :class="(n>voto(filmSelez.vote_average))? 'fa-regular yellow': 'fa-solid yellow'"></i>
                </div>
            </li>
            
        </ul>

        <ul>
            <h1>SerieTv</h1>
            <li v-for="(serieSelez, index) in serieTv" :key="index">
                {{serieSelez.name}}-
                {{serieSelez.original_name}}-
                <img :src="bandiera(serieSelez.original_language)" alt=""/>-
                {{voto(serieSelez.vote_average)}}
                <img :src="'http://image.tmdb.org/t/p/w185/' + serieSelez.poster_path" alt=""/>
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
          
        }
    },
    methods:{
       voto(voto){
            let voti= voto /2;
            return voti.toFixed();
           
        },
        bandiera(lingua){
            let bandiera=lingua;
            if(bandiera=='en'){
                bandiera='gb'
            }else if(bandiera=="zh"){
                bandiera="cn"
            } else if(bandiera=="ja"){
                bandiera="jp"
            }else if(bandiera=="ta"){
                bandiera="th"
            } else if(bandiera=="ko"){
                bandiera="kr"
            }
            let flag= 'https://flagcdn.com/24x18/'+ bandiera +'.png';
           
            return flag
            
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

    .yellow{
        color:rgb(253, 253, 9)
    }

</style>
