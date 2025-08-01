<template>
    <div class="usersDaten">
        🍎🍐🍊🍒🥦
        <p>{{ user.name }}</p>
        <p>{{ user.email }}</p>
        <p>{{ user.password }}</p>
    </div>
</template>

<script>
    export default {
        props: {
            user: {
                type: Object,
                required: true,
            },
        },
    };
</script>

<style></style>
