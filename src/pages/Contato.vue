<template>
    <main>

        <section class="container">
            <h1>Contato</h1>
          
                <div class="contacts" v-for="(contact,index) in contacts" :key="index"> 
                    <h3>{{contact.title}}</h3>
                    <a :href="contact.link" target="_blank">
                        {{contact.link}}
                    </a>
                </div>
            
        </section>

    </main>
</template>

<script>
import api from '@/services/api.js';

export default {
    name: 'Contato',
    data(){
        return{
            contacts:[]
        }
    }, 
    mounted(){
        api.get('/contacts.json').then(response=>{
            this.contacts = response.data;
        })
    }
}
</script>
<style scoped>
    main{
        align-items:center;
    }
    .contacts{
        margin-bottom: 40px;
        color:var(--color-text-dark);
    }
    .contacts a{
        color:var(--color-text-dark);
    }

</style>
