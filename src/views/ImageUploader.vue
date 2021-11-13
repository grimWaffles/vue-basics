<template>
    <h3>Image Uploader</h3>
    <hr><br>
    <h2>Upload  Student  ID image:</h2>
    <br>
    
    <div class="image-uploader">
        <div id="preview">
            <img :src="url!=null? url : defImg " class="img-preview" @click="imageClicked('imageUploadInput')"/>
        </div>
        <i>Image should  be under 2MB in size</i>
        <br><br>

        <input type="file" @change="onFileSelected" id="imageUploadInput" ref="imgToUpload" v-show="false">
        <button class="btn btn-primary img-button" @click="onUpload">Upload File</button>
        <button class="btn btn-primary" @click="removeImage">Remove</button>
    </div>

</template>

<script>

export default{
    name: "ImageUploader",
    data(){
        return {
            selectedFile:null,
            url:null,
            defImg:require("../assets/logo.png")
        }
    },
    methods:{
        onFileSelected(event){
            console.log(event.target.files[0])
            this.selectedFile=event.target.files[0]
            this.url=URL.createObjectURL(this.selectedFile)
        }, 
        removeImage(){
            if(this.selectedFile!=null){
                this.selectedFile=null
                this.url=null
                this.$refs.imgToUpload.value=null
            }
        },
        imageClicked(inputElement){
            document.getElementById(inputElement).click()
        },
        onUpload(){
            
        },
    }
};

</script>

<style>
.img-preview{
    height: 250px;
    width:250px;
}
.img-button{
    margin-right: 10px;
    color: white;
    background: black;
}
</style>
