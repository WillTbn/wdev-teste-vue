<template>
    <footer>
        <a class="sociallink" v-for="(socialLink,index) in socialLinks" :key="index" :href="socialLink.link">
            <img :src="socialLink.icon" :title="socialLink.label" :alt="socialLink.label" target="_blank">
        </a>
        
    </footer>
</template>
<script>
import api from '@/services/api.js';

export default{
    name: 'Footer',
    data(){
        return {
            socialLinks: []
        }
    },
    mounted(){
        api.get('/social-links.json').then(response => {
            this.socialLinks = response.data;
        });
    }
}
</script>
<style scoped>
footer{
    width:100%;
    height: 60px;
    background-color: var(--color-background-nav);
    display:flex;
    justify-content: center;
    align-items: center;
}
.sociallink{
    border: 2px solid var(--color-text-light);
    display: flex;
    justify-content: center;
    align-items: center;
    border-radius: 50%;
    width: 40px;
    height: 40px;
    margin:0 10px;
}
.sociallink img{
    width:20px;
}
</style>
