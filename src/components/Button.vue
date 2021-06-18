<template>
    <button :click="onClick()" :style="{background: color}" class="btn">
        {{openingText}}
    </button>    
</template>

<script>
    export default{
        name:'Button',
        props:{
            openingText:String,
            color:String,
            
        },
        methods:{
            onClick(){
                console.log("Click!")
                
            }
        }
    }
</script>

<style>

</style>