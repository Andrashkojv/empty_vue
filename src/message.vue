<template>
    <p> {{text}} </p>
</template>

<script>
export default {
    data:function(){
        return{
            text:this.defaultText 
        }
    },
    props:{
        defaultText:String
    }
}
</script>

<style scoped>
    p{
        color: blue;
    }
</style>