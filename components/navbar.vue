<template>
    <header class="navbar">
        <nuxt-link to="/">
            <img :src="logo" class="logo">
        </nuxt-link> 
            <div class="social-icon">
                <a href="https://vk.com/id131528319">
                    <img :src="vk" class="logo social">
                </a> 
                <a href="https://www.instagram.com/victorium__/">
                    <img :src="instagram" class="logo social">
                </a>
                <a href="https://twitter.com/Viikonda">
                    <img :src="twitter" class="logo social">
                </a>
            </div>
            <ul class="navbar__links" >
                <li v-for="titles in title" :key="titles.id"><a href="#">{{ titles.title }}</a></li>
            </ul>
    </header>
</template>

<script>
import logo from '../src/img/pencil.png'
import vk from '../src/img/vk.png'
import instagram from '../src/img/instagram.png'
import twitter from '../src/img/twitter.png'

export default {
    data: () => ({ 
        logo,
        vk,
        instagram,
        twitter,
        title: [
            {id: 1, title: "Главная"},
            {id: 2, title: 'Комментарии'},
            {id: 3, title: 'Связь'}
        ]
}),
 
}
   
</script>

<style lang='scss'>
@media (max-width: 770px){
    .navbar__links{
        li{
            font-size: 16px;
            a{
                color: #fff;
            }
            padding: 10px;   
        }
    }
        .logo.social{
            width: 50px;
            height: 50px;
        }
        .logo{
            width: 50px;
            height: 50px;
        }
}
.logo{
    max-width: 80px;
    max-height: 80px;
    border-radius: 50%;
}

.social-icon{
    position: fixed;
    left: 50%;
    margin-left: -150px;
    transition: 1.5s;
    opacity: 0;
}

.social-icon.active{
    left: 16px;
    top: 25%;
    transition: 1.5s;
    display: flex;
    margin-left: 0;
    flex-direction: column;
    opacity: 1;
}

.social{
    margin-right: 20px;
    margin-top: 20px;
}

.navbar{
    display: flex;
    padding: 1rem;
    justify-content: space-between;
    align-items: center;
    // background: linear-gradient(329deg, rgba(0,95,255,1) 0%, rgba(23,81,102,1) 100%);
}

.navbar__links{
    display: flex;
    justify-content: space-between;
    font-size: 24px;
    li{
        a{
            color: #fff;
        }
        padding: 10px;
        
    }
}
</style>