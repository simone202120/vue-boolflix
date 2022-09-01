<template>
  <header>
    <div class="container flex">
        <div>
            <img id="logo" src="../assets/netflix_preview_rev_1.png" alt="">
        </div>
        <div>
            <input type="text" v-model="imputText">
            <button @click="$emit ('search', imputText)">Cerca <i class="fa-solid fa-magnifying-glass"></i></button>
        </div>

    </div>
  </header>
</template>

<script>
export default {
    name: 'MyHeader',
    data(){
        return{
            imputText:""
        }
    }
}

</script>

<style lang="scss">
    @import '../style/general.scss';

    header{
        padding: 20px 0;
        background-color:#171717;
        text-align: right;

        input{
            
            margin-right: 10px;
            padding: 5px;
        }
    }

    button{
        padding: 5px;
        font-size: 15px;
        font-weight: bold;
        color: white;
        background-color: red;
        border-color: rgba(255, 0, 0, 0.678);
    }
    .flex{
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    #logo{
        height: 40px;
    }

</style>