<template>
    <header>
        <h1>{{title}}</h1>
        <Button :openingText="btnText" @click="btnOnClick"/>
    </header>
</template>

<script>

import Button from './Button'

export default{
        name:'Header',
        props:{
            title:String,
            btnText:String
        },
        components:{
            Button
        },
        methods:{
            btnOnClick(){
                this.$emit('toggle-add-task')
            }
        }
    }
</script>

<style scoped>

</style>