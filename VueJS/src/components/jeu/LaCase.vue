<template>
    <button @click="clickMe">
        <img v-if="!imageurl==''" :src="require('@/assets' +  imageurl)" />
        <h2 v-if="imageurl==''">Caché !!!</h2>
    </button>
</template>

<script>
const urlours = '/img/giphy.gif'
const urlf1 = '/img/giphy.webp'
export default {
    props: {
        image : String,
        id : String
    },
    computed: {
        imageurl: function(){
            if (this.image == '') {
                //this.affichage = false;
                return '';
            } else {
                //this.affichage = true;
                if (this.image == 'ours') {
                    return urlours; 
                }
                if (this.image == 'f1') {
                    return urlf1; 
                }
                return '';
            }
        }
    },
    methods: {
        clickMe(){
            this.$emit('clickCase',this.id);
        }
    }
}
</script>