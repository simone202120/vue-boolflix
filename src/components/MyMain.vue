<template>
    <main>

        <h1>FILM</h1>

        <div class="container flex">
            <div v-for="(filmSelez,index) in filmList" :key="index" class="card flip-card">
                <div class="flip-card-inner">
                    <div class="poster flip-card-front">
                        <img :src="'http://image.tmdb.org/t/p/w185/' + filmSelez.poster_path" alt=""/>
                    </div>

                    <div class="info flip-card-back">
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
        </div>

        <h1>SERIETV</h1>

        <div class="container flex">
            <div v-for="(serieSelez,index) in serieTv" :key="index" class="card flip-card">
             <div class="flip-card-inner">
                    <div class="poster flip-card-front">
                        <img :src="'http://image.tmdb.org/t/p/w185/' + serieSelez.poster_path" alt=""/>
                    </div>

                    <div class="info flip-card-back">
                        <h4>TITLE:</h4><p>{{serieSelez.name}}</p>
                        <h4>ORIGINAL TITLE:</h4> <p>{{serieSelez.original_name}}</p>

                        <div>
                            <h4>VOTO</h4>
                            <i v-for="x in 5" :key='x' class="fa-star" :class="(x>voto(serieSelez.vote_average))? 'fa-regular yellow': 'fa-solid yellow'"></i>
                        </div>

                        <div class="overview">
                            <h4>OVERVIEW:</h4>
                            <p>{{serieSelez.overview}}</p>
                        </div>

                        <H4>ORIGINAL LANGUAGE</H4>
                        <img class="lingua" :src="bandiera(serieSelez.original_language)" alt=""/>
                    </div>
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
    .flip-card-inner{
        position: relative;
        width: 100%;
        height: 100%;
        transition: transform 0.8s;
        transform-style: preserve-3d;
    }
    .card{
        width:calc(100% / 5);
        height: 400px;
        padding: 5px;
        margin-top: 10px;
        perspective: 1000px;
        
        
        .overview{
            overflow-y: auto;
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
        transition-duration: 0.5s;
        height: 100%;
        
        img{
            height: 100%;
            object-fit: cover;
            width: 100%;
        }

    }
       
    .flip-card:hover .flip-card-inner {
        transform: rotateY(180deg);
    }

    .flip-card-front, .flip-card-back {
        position: absolute;
        width: 100%;
        height: 100%;
        backface-visibility: hidden;
    }

    .flip-card-front {
        background-color: #bbb;
        color: black;
    }

    .flip-card-back {
        background-color:  #171717;
        color: white;
        transform: rotateY(180deg);
    }
    ::-webkit-scrollbar {
        width: 5px;
    }

    ::-webkit-scrollbar-track {
        box-shadow: inset 0 0 5px grey; 
        border-radius: 10px;
    }
    
    ::-webkit-scrollbar-thumb {
        background: rgba(255, 0, 0, 0.71); 
        border-radius: 10px;
    }


</style>
