<template>
    <section class="container">
        <div class="image-box" 
                v-for="img in imgs" 
                :key="img.id">
            <img 
                :src="img.img" 
                class="image">
            <label class="box-title">{{img.title}}</label>
            <nuxt-link to="/photos"><button @click.prevent="openPhotos(img.id)" class="btn">Посмотреть</button></nuxt-link> 
        </div>
       
    </section>
</template>

<script>
import img1 from '../src/img/img1.jpg'
import img2 from '../src/img/img2.jpg'
import img3 from '../src/img/img3.jpg'
import img4 from '../src/img/img4.jpg'
export default {
    data: () => ({  
        imgs: [
            {id: 1,img: img1, title: 'Красота в глазах смотрящего.'},
            {id: 2,img: img2, title: 'Глаза-океаны, а в них крушение.'},
            {id: 3,img: img3, title: 'Закрой глаза. Так лучше видно.'},
            {id: 4,img: img4, title: 'И взмах ее ресниц решил его судьбу…'}
        ]
        }
        
),
    methods: {
        openPhotos(id) {
            this.$router.push('/photos/' + id)
        }
    }
}
</script>

<style lang="scss">



.container{
    max-width: 1200px;
    margin: 0 auto;
}
.title{
    display: flex;
    justify-content: center;
    align-items: center;
    color: #fff;
    font-size: 32px;
    margin-top: 150px;
}
.image{
    max-width: 1200px;
    max-height: 1200px;
    
}
.subtitle{
    font-size: 24px;
}
.image-box{
    display: flex;
    flex-direction: column;
    margin: 0 auto;
    align-items: center;
    max-width: 1050px;
    color: #fff;
    padding: 50px 0 50px 0;
}

.box-title{
    padding: 25px 0;
    font-size: 2rem;
}

.btn{
    width: 150px;
    height: 50px;
    border-radius: 15px;
    background: rgb(174,235,238);
    background: linear-gradient(315deg, rgba(174,235,238,1) 0%, rgba(2,117,236,0.3225665266106442) 31%);
}

@media (max-width: 770px){
    .image{
        width: 400px;
    }
}
@media (max-width: 430px){
    .image{
        width: 300px;
    }
    .box-title{
        padding: 10px 0;
        font-size: 1.5rem
    }
}
</style>