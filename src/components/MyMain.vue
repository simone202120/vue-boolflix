<template>
    <main>
        <div class="container">
            <h1>FILM</h1>
            <div v-for="(filmSelez,index) in filmList" :key="index" class="card">
                <h4>TITOLO:{{filmSelez.title}}</h4>
                <h4>TITOLO ORIGINLE:{{filmSelez.original_title}}</h4>
                <div>
                    <i v-for="n in 5" :key='n' class="fa-star" :class="(n>voto(filmSelez.vote_average))? 'fa-regular yellow': 'fa-solid yellow'"></i>
                </div>
                <h4>OVERVIEW:{{filmSelez.overview}}</h4>
                <img :src="bandiera(filmSelez.original_language)" alt=""/>
            </div>
            
            <h1>serieTV</h1>
            <div v-for="(serieSelez, id) in serieTv" :key="id" class="card">
                <h4>TITOLO:{{serieSelez.name}}</h4>
                <h4>TITOLO ORIGINLE:{{serieSelez.original_name}}</h4>
                <div>
                    <i v-for="x in 5" :key='x' class="fa-star" :class="(x>voto(serieSelez.vote_average))? 'fa-regular yellow': 'fa-solid yellow'"></i>
                </div>
                <h4>OVERVIEW:{{serieSelez.overview}}</h4>
                <img :src="bandiera(serieSelez.original_language)" alt=""/>
            </div>
        </div> 
    </main>
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
    main{
        background-color: #171717;
        color:white
    }

    .yellow{
        color:rgb(253, 253, 9)
    }

</style>
