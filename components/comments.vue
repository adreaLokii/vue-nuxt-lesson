<template>
    <div>
        <div id="comments">
            <input @submit.prevent type="text" class="comments__input" placeholder="Введите комментарий">
            <button class="comments__btn" @click="pushUsers()">Отправить</button>
        </div>
        <div class="comments" v-for="user in users" :key="user.id">
            <div>
                <img :src="userAvatar" class="comments__avatar">
            </div> 
            <div>
                <p class="comments__body">{{user.body}}</p>
            </div> 
        </div>
    </div>
    
</template>

<script>
import userAvatar from '../src/img/user.png'
export default {
    
    data: () => ({
        userAvatar,
        users: [],
    }),
    async mounted() {
        let users = await this.$axios.$get('https://jsonplaceholder.typicode.com/comments?postId=2')
        console.log(users)
        let newUsers = this.users
        this.users = [...newUsers, ...users]
        console.log(this.users)
    },
    methods: {
        pushUsers () {
            let input = document.querySelector('.comments__input')
            const newPost = {
                postId: 2,
                id: Date.now(),
                name: 'Emin',
                email: 'gqgqgt@qgqg.ru',
                body: input.value
            }
            this.users.push(newPost)
            input.value = ''
            console.log(this.users)
        }
    }
}
</script>

<style scoped lang="scss">
.comments{
    width: 75%;
    margin: 0 auto;
    font-size: 20px;
    background-color: #e6e1e1;
    display: flex;
    padding: 15px;
    &__avatar{
        width: 100px;
        height: 100px;
    }

    &__body{
        width: 70%;
        padding: 1rem;
    }

    &__email{
        padding: 0 1rem 1rem 1rem;
    }

    &__name{
        padding: 1rem;
    }
}
.comments__input{
        margin: 0 0 0.5rem 12.5%;
        padding: 0.5rem;
    }

@media (max-width: 770px){
    .comments__body{
        font-size: 1rem;
    }
    .comments__avatar{
        width: 50px;
        height: 50px;
    }
}
</style>