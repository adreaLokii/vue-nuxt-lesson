<template>
    <section @mouseenter="fixedIcons()">
        <nuxt-link to="/">
                    <img :src="logo" class="logo photo">
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
        <img :src="namePhoto($route.params.id).img" class="avatar">
        <nuxt-link :to="nextPhoto($route.params.id)">
            <img :src="next" class="next" @click="nextPhoto($route.params.id)">
        </nuxt-link>
        <nuxt-link :to="prevPhoto($route.params.id)">
            <img :src="prev" class="prev" @click="prevPhoto($route.params.id)">
        </nuxt-link>
        
        
        <div class="supertitle">
            <h1>{{namePhoto($route.params.id).title}}</h1>
        </div>
        
    </section>
</template>

<script>
import img1 from '../../src/img/img1.jpg'
import img2 from '../../src/img/img2.jpg'
import img3 from '../../src/img/img3.jpg'
import img4 from '../../src/img/img4.jpg'
import vk from '../../src/img/vk.png'
import instagram from '../../src/img/instagram.png'
import twitter from '../../src/img/twitter.png'
import logo from '../../src/img/pencil.png'
import next from '../../src/img/next.svg'
import prev from '../../src/img/prev.svg'
export default {
    components:{

    },
    data: () => ({  
        img1,
        img2,
        img3,
        img4,
        vk,
        instagram,
        twitter,
        logo,
        next,
        prev,
        imgs: [
            {id: 1,img: img1, title: 'Красота в глазах смотрящего.'},
            {id: 2,img: img2, title: 'Глаза-океаны, а в них крушение.'},
            {id: 3,img: img3, title: 'Закрой глаза. Так лучше видно.'},
            {id: 4,img: img4, title: 'И взмах ее ресниц решил его судьбу…'}
        ]
        }
        
),
    methods: {
        namePhoto(id) {
            let photo = this.imgs.filter(img => img.id == id)
            return  photo[0]
        },
        nextPhoto(id) {
            if(Number(id) === this.imgs.length){
                console.log('ggg')
                return "./4"
            }
            else{
                let photo = this.imgs.filter(img => img.id == id)
                let strPhoto = String(photo[0].id + 1)
                let nextPhoto = "./" + strPhoto
                return nextPhoto
            }  
        },
        prevPhoto(id){
            if(Number(id) === 1){
                console.log('ggg')
                return "./1"
            }
            else{
                let photo = this.imgs.filter(img => img.id == id)
                let strPhoto = String(photo[0].id - 1)
                let prevPhoto = "./" + strPhoto
                return prevPhoto
            }
        },
        fixedIcons() {
            document.querySelector('.social-icon').classList.add('active')
            document.querySelector('.supertitle').classList.add('active')
        }
    }
}
</script>

<style scoped>
.avatar{
    width: 100%;
    height: 100%;
}
.supertitle{
    position: fixed;
    z-index: 1;
    left: 50%;
    top: 1%;
    font-size: 50px;
    opacity: 1;

}
.supertitle.active{
    opacity: 0;
    transition: 5.5s;
}
.photo{
    position: fixed;
    left: 16px;
    top: 16px;
}

.next{
    width: 100px;
    height: 100px;
    position: fixed;
    right: 16px;
    margin-bottom: -50px;
    bottom: 50%;
}

.prev{
    width: 100px;
    height: 100px;
    position: fixed;
    left: 86px ;
    margin-bottom: -50px;
    bottom: 50%;
}

@media (max-width: 770px){
    .next{
        z-index: 1;
        width: 50px;
        height: 50px;
    }
    .prev{
        z-index: 1;
        width: 50px;
        height: 50px;
    }
    .supertitle{
        font-size: 30px;
    }
}
</style>