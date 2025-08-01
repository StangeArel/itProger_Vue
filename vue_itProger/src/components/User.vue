<template>
    <div class="usersDaten">
        <p>{{ user.name }}</p>
        <p>{{ user.email }}</p>
        <p>{{ user.password }}</p>
        <button @click="handleDelete">Löschen</button>
    </div>
</template>

<script>
    export default {
        props: {
            user: {
                type: Object,
                required: true,
            },
            index: {
                type: Number,
                required: true,
            },
            deleteUser: {
                type: Function,
                required: true,
            },
        },
        methods: {
            handleDelete() {
                console.log('🌶️');
                this.deleteUser(this.index);
            },
        },
    };
</script>

<style scoped>
    button {
        background-color: red;
        color: white;
        border: none;
        padding: 5px 10px;
        cursor: pointer;
        border: 2px solid darkred;
    }

    button:hover {
        background-color: darkred;
    }
</style>
