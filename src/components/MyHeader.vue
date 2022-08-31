<template>
  <header>
    <input type="text" v-model="imputText">
    <button @click="$emit ('search', imputText)">Cerca</button>

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
        height: 100px;
        background-color:black;
        text-align: right;

        input{
            margin-top:40px;
        }
    }
</style>