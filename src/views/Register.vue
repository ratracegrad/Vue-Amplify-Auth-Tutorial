<template>
    <div class="container">
        <form @submit.prevent="register">
            <h2>Register</h2>
            <input
                type="email"
                v-model="email"
                placeholder="Email address..."
            />
            <input
                type="password"
                v-model="password"
                placeholder="password..."
            />
            <button>Register</button>
        </form>
    </div>
</template>

<script>
import { Auth } from 'aws-amplify';

export default {
    name: 'Register',
    data() {
        return {
            email: '',
            password: '',
        };
    },
    methods: {
        async register() {
            try {
                await Auth.signUp({
                    username: this.email,
                    password: this.password,
                });
                alert('User successfully registered. Please login');
            } catch (error) {
                alert(error.message);
            }
        },
    },
};
</script>
