<template>
    <div class="post">
        <div>
            <div><strong>Номер: </strong>{{ post.id }} Likes = {{ $store.state.likes }}</div>
            <div><strong>Название: </strong>{{ post.title }}</div>
            <div><strong>Описание: </strong>{{ post.body }}</div>
        </div>
        <div class="post__btns">
            <my-button
                @click="$router.push(`/post/${post.id}`)"
            >
                Открыть
            </my-button>
            <!-- Кавычки должны быть ` а не ' или " для передаваемых параметров !!! -->
            <my-button
                @click="$emit('remove', post)"
                class="remove"
            >
                Удалить
            </my-button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        post: {
            type: Object,
            required: true,
        }
    }
}
</script>

<style scoped>
.post {
    padding: 15px;
    border: 2px solid teal;
    align-self: flex-end;
    margin-top: 15px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.post__btns {
    display: flex;
}
.remove {
    color: darkred;
    border: 1px solid darkred;
}
.remove:hover {
    color: red;
    border: 1px solid red;
}
</style>