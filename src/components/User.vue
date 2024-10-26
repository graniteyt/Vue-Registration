<template>
    <div class="output">
        <button @click="deleteUser(index)">Удалить</button>
        <h3>{{ user.name }}</h3>
        <p>{{ user.pass }} - <b>{{ user.mail }}</b></p>
    </div>
</template>

<script>
export default {
    props: {
        user: {
            type: Object,
            required: true
        },
        index: {
            type: Number,
            required: true
        },
        deleteUser: {
            type: Function,
            required: true
        }
    }
}
</script>

<style scoped>
.output {
    margin-top: 10px;
    padding: 15px;
    background-color: rgb(220, 220, 220);
    box-shadow: 4px 4px 8px 0px rgba(34, 60, 80, 0.2);
    border-radius: 10px;
    font-size: 22px;
    width: auto;
    border: 1px black solid;
    max-width: fit-content;
    font-family: 'Franklin Gothic Medium', 'Arial Narrow', Arial, sans-serif;
    transition: 0.5s;
}

.output:hover {
    transform: translateY(-5px);
}
</style>
