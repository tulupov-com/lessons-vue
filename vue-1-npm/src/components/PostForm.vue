<template>
    <form @submit.prevent>
        <my-input 
            :value="post.outTitle"
            @input="post.outTitle = $event.target.value"
            placeholder="Название" 
        />

        <my-input 
            v-model="post.outBody"
            placeholder="Описание" 
        />
        <!-- можно просто использовать v-model вместо v-bind + v-on (как выше для title) -->
        <!-- можно добавить v-model:value="post.outBody" чтобы value тоже менялось -->
        <my-button 
            @click="createPost"
            style="margin-top: 1rem; align-self: flex-end;"
        >Добавить</my-button>
        <!-- не забыть type="button" чтобы страница не перерисовывалась -->
    </form>
</template>

<script>
export default {
    data() {
        return {
            post: {
                outTitle: '',
                outBody: ''
            }
        }
    },
    methods: {
        createPost() {
            this.post.id = Date.now();
            this.$emit('create', this.post, 'second param', 'third param')
            this.post = {
                outTitle: '',
                outBody: ''
            }  
        }
    }
}
</script>

<style scoped>
form {
    display: flex;
    flex-direction: column;
}
</style>