<template>
    <header>
        <nav class="container">
            <router-link to="/">
                <img src="https://camo.githubusercontent.com/069f07451e482c652fb105fc14f1b548223b08462bf9e18ddf8ef361de887519/687474703a2f2f776f7a612e636f6d2e62722f776f7a612e706e67" alt="woza" id="logo" srcset="" width="160px" height="50px">
            </router-link>
            
            <a alt="abrir menu" v-on:click="openMenu" id="menu-button">
                <svg xmlns="http://www.w3.org/2000/svg" width="36" height="36" fill="#fff" class="bi bi-list" viewBox="0 0 16 16">
                    <path fill-rule="evenodd" d="M2.5 12a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5zm0-4a.5.5 0 0 1 .5-.5h10a.5.5 0 0 1 0 1H3a.5.5 0 0 1-.5-.5z"/>
                </svg>
            </a>
            <div id="menu-overlay" v-on:click="closeMenu" v-if="menuActive"></div>
            <div id="menu-items" :class="{active:menuActive}">
                <img src="https://camo.githubusercontent.com/069f07451e482c652fb105fc14f1b548223b08462bf9e18ddf8ef361de887519/687474703a2f2f776f7a612e636f6d2e62722f776f7a612e706e67" alt="woza" id="menu-logo" srcset="" width="110px" height="50px">
                <ul>
                    <li v-on:click="closeMenu"><router-link to="/">Home</router-link></li>
                    <li v-on:click="closeMenu"><router-link to="/videos">Videos</router-link></li>
                    <li v-on:click="closeMenu"><router-link to="/sobre">Sobre</router-link></li>
                    <li v-on:click="closeMenu"><router-link to="/contato">Contato</router-link></li>
                </ul>   
            </div>
        </nav>
    </header>
</template>
<script>
export default {
    name: 'Header',
    data(){
        return{
            menuActive: false
        }        
    },
    methods:{
        openMenu:function(){
            this.menuActive = true;
        },
        closeMenu:function(){
            this.menuActive = false;
        }
    }
}
</script>
<style scoped>
    header{
        background-color: var(--color-background-nav);
        width:100%;
        height: 60px;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    nav{
        display: flex;
        justify-content: space-between;
    }
    #menu-button{
        width:30px;
    }
    #menu-overlay{
        position: fixed;
        top:0;
        left: 0;
        width: 40%;
        height: 100vh;
        background-color: #000;
        opacity:0.8;
    }
    #menu-items{
        position: fixed;
        top:0;
        right: 0;
        background-color: var(--color-background-nav);
        width:60%;
        height: 100vh;
        display: none;
        flex-direction: column;
        justify-content: flex-start;
        align-items: center;
    }
    #menu-items.active{
        display: flex;
    }
    ul{
        list-style: none;
        text-align: center;
    }
    ul li a{
        color: var(--color-text-light);
    }
    ul li{
        margin: 20px 0px;
    }
    #menu-logo{
        margin-top:1rem;
        margin-bottom:1rem;
    }
    @media (min-width:700px){
        #menu-button,
        #menu-logo,
        #menu-overlay{
            display: none;
        }
        #menu-items{
            display:flex;
            position:static;
            height: 60px;
            width: auto;
        }
        ul{
            display: flex;
            height: 60px;
            align-items: center;
        }
        ul li{
            margin:0;
            margin-left:20px;
        }
    }
</style>
