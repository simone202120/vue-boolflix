<template>
    <main>
        <h1>FILM</h1>

        <div class="container flex">
            <div v-for="(filmSelez,index) in filmList" :key="index" class="card">
                <div class="poster">
                    <img :src="'http://image.tmdb.org/t/p/w185/' + filmSelez.poster_path" alt=""/>
                </div>
                <div class="info">
                    <h4>TITLE:</h4><p>{{filmSelez.title}}</p>
                    <h4>ORIGINAL TITLE:</h4> <p>{{filmSelez.original_title}}</p>
                    <div>
                        <h4>VOTO</h4>
                        <i v-for="n in 5" :key='n' class="fa-star" :class="(n>voto(filmSelez.vote_average))? 'fa-regular yellow': 'fa-solid yellow'"></i>
                    </div>
                    <div class="overview">
                        <h4>OVERVIEW:</h4>
                        <p>{{filmSelez.overview}}</p>
                    </div>
                    <H4>ORIGINAL LANGUAGE</H4>
                    <img class="lingua" :src="bandiera(filmSelez.original_language)" alt=""/>
                </div>
                
            </div>
        </div>

        <h1>SERIETV</h1>

        <div class="container flex">
            <div v-for="serieSelez in serieTv" :key="serieSelez.id" class="card">
                <div class="poster">
                    <img :src="'http://image.tmdb.org/t/p/w185/' + serieSelez.poster_path" alt=""/>
                </div>
                <div class="info">
                    <h4>TITOLO:</h4> <P>{{serieSelez.name}}</P>
                    <h4>TITOLO ORIGINLE:</h4> <p>{{serieSelez.original_name}}</p>
                <div>
                    <h4>VOTO</h4>
                    <i v-for="x in 5" :key='x' class="fa-star" :class="(x>voto(serieSelez.vote_average))? 'fa-regular yellow': 'fa-solid yellow'"></i>
                </div>
                <div class="overview">
                    <h4>OVERVIEW:</h4>
                    <P>{{serieSelez.overview}}</P>
                </div>
                <H4>ORIGINAL LANGUAGE</H4>
                <img :src="bandiera(serieSelez.original_language)" alt=""/>
                </div>
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
        color:white;
        min-width: none;
    }

    .yellow{
        color:rgb(253, 253, 9)
    }
    .flex{
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
    }
    .card{
        width:calc(100% / 5);
        height: 400px;
        padding: 5px;
        margin-top: 10px;
        &:hover .poster{
            display: none;
            
        }
        &:hover .info{
            transform: rotateX(180deg) 1;
            display: inline-block;
            
            
        }
        .overview{
            overflow-y: scroll;
            max-height: 150px;
        }
        H4{
            margin-top: 10px;
            font-size: 15px;
        }
        p{
            font-size: 12px;
        }
        .lingua{
            margin-left: 40%;
            margin-top: 15px;
        }
    }
    h1{
        margin-left: 70px;
    }
    .poster{
        height: 100%;
        
        img{
            height: 100%;
            object-fit: cover;
            width: 100%;
        }

    }
    .info{
        display: none;
    }


</style>
