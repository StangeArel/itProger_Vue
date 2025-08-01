<template>
    <form @submit.prevent="sendData">
        <input type="text" v-model="userName" placeholder="Name *" />
        <p className="error">{{ errorName }}</p>
        <input type="password" v-model="userMail" placeholder="Email *" />
        <p className="error">{{ errorMail }}</p>
        <input type="email" v-model="userPassword" placeholder="Password *" />
        <p className="error">{{ errorPassword }}</p>
        <button @click="sendData()" type="submit">Versenden</button>
    </form>
    <p><b>Name:</b> {{ userName }}</p>
    <p><b>Email:</b> {{ userMail }}</p>
    <p><b>Password:</b> {{ userPassword }}</p>
    <p className="users">
        <u>{{ users }}</u>
    </p>
    <div v-if="users.length == 0" className="usersDatenTwo">
        Derzeit sind keine Benutzer vorhanden 📝
    </div>
    <div v-else-if="users.length == 1" className="usersDatenTwo">
        Users has only 1️⃣ element
    </div>
    <div v-else-if="users.length == 2" className="usersDatenTwo">
        Users has 2️⃣ element
    </div>
    <div v-else className="usersDatenTwo">
        ‼️ Users has more than 2 element ❗️
    </div>
    <User
        v-for="(el, index) in users"
        :key="index"
        :user="el"
        :index="index"
        :deleteUser="deleteUser"
    />
</template>

<script>
    import User from './components/User.vue';

    export default {
        components: {
            User,
        },

        data() {
            return {
                users: [],
                errorName: '',
                errorMail: '',
                errorPassword: '',
                userName: '',
                userMail: '',
                userPassword: '',
            };
        },
        methods: {
            sendData() {
                if (this.userName === '') {
                    this.errorName = '* Please fill your Name';
                    return;
                } else if (this.userMail === '') {
                    this.errorMail = '* Please fill your Email';
                    return;
                } else if (this.userPassword === '') {
                    this.errorPassword = '* Please fill your Password';
                    return;
                } else {
                }
                this.errorName = '';
                this.errorMail = '';
                this.errorPassword = '';
                console.log('🦊 Name:', this.userName);
                console.log('🦊 Email:', this.userMail);
                console.log('🦊 Password:', this.userPassword);
                this.users.push({
                    name: this.userName,
                    email: this.userMail,
                    password: this.userPassword,
                });
            },
            deleteUser(index) {
                this.users.splice(index, 1);
            },
        },
    };
</script>

<style>
    form {
        background-color: greenyellow;
        display: flex;
        flex-direction: column;
        width: 50%;
        text-align: center;
        justify-content: center;
        align-items: center;
        margin: 20px auto;
        padding: 20px;
        border-radius: 30px;
        gap: 10px;
    }

    p {
        text-align: center;
        font-size: 20px;
        color: red;
    }

    button {
        background-color: green;
        cursor: pointer;
    }

    button:hover {
        background-color: rgb(176, 240, 80);
    }

    .users {
        font-size: 20px;
        color: blue;
        text-align: center;
    }

    .usersDaten {
        background-color: lightblue;
        color: blue;
        padding: 10px;
        margin: 10px auto;
        width: 50%;
        border-radius: 10px;
        text-align: center;
    }

    .usersDatenTwo {
        background-color: rgba(243, 133, 133, 0.476);
        color: red;
        padding: 10px;
        margin: 10px auto;
        width: 50%;
        border-radius: 10px;
        text-align: center;
    }
</style>
