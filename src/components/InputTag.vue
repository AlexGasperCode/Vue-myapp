<script>
export default {
    data(){
        return {
        //2 propiedades
            currentValue:"",
            tags:[],
        }
    },
    methods:{ //Creamos un evento
        handleKeyDown(e){
            if(e.key = 'Enter' && this.currentValue != ``){
                this.tags.push(this.currentValue);
            }
        },
        handleSubmit(){
            if(this.currentValue != ""){
                this.tags.push(this.currentValue);
                //Borrar valor actual
                this.currentValue = "";
        }
        },
        deleteTag(tag){
            this.tags = this.tags.filter((item) => item != tag);
        },
    },
};
</script>
<template>
    <div class="inputTag">
        <div class="tags">
            <div class="tag" v-for="(tag , index) in tags" :key="index">
            <!--El valor de tag-->
            {{ tag }}<button @click="deleteTag(tag)">X</button>
            </div>
        </div>
        <!-- Prevent omitir el comportamiento de mi formulario -->
        <form @submit.prevent="handleSubmit">
        <input type="text" v-model="currentValue" @keydown="handleKeyDown"/>
        </form>
    </div>
</template>
<style scoped></style>