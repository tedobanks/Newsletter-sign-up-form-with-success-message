<script setup>
import { defineProps } from 'vue'

const { email } = defineProps(['email'])
</script>

<template>
    <main>
        <div class="container">
            <div class="message-body">
                <img src="../assets/images/icon-success.svg" alt="">
                <h1>Thanks for subscribing!</h1>
                <p>A confirmation email has been sent to <span>{{ email }}</span>.
                    Please open it and click the button inside to confirm your subscription.</p>
            </div>
            <div class="btn-container">
                <button>Dismiss message</button>
            </div>
        </div>
    </main>
</template>

<style scoped>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

main {
    min-height: 100vh;
    height: 100vh;
    width: 100%;
    display: flex;
    align-items: start;
    justify-content: center;
}

.container {
    height: 100%;
    width: 100%;
}

.message-body {
    height: 80%;
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: start;
    padding: 0px 20px 0px 20px;
}

.message-body img {
    width: 60px;
    margin-bottom: 20px;
}

.message-body h1 {
    font-family: 'Roboto', sans-serif;
    color: hsl(234, 29%, 20%);
    font-weight: 700;
    font-size: 40px;
    margin-bottom: 20px;
    line-height: 1;
}

.message-body p {
    font-family: 'Roboto', sans-serif;
    color: hsl(234, 29%, 20%);
    font-weight: 400;
    font-size: 16px;
}

.message-body p span {
    font-weight: 700;
}

.btn-container {
    height: 20%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0px 20px 0px 20px;
}

.btn-container button {
    height: 50px;
    width: 100%;
    border-radius: 10px;
    font-family: 'Roboto', sans-serif;
    font-weight: 700;
    font-size: 16px;
    color: hsl(0, 0%, 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    background-color: hsl(234, 29%, 20%);
    border: none;
}

@media only screen and (min-width: 768px) {
    main {
        align-items: center;
        background-color: hsl(235, 18%, 26%);
    }

    .container {
        height: 350px;
        width: 350px;
        border-radius: 20px;
        padding: 20px;
        background-color: white;
    }

    .message-body img{
        width: 50px;
    }
    .message-body h1{
        font-size: 35px;
    }

    .message-body p{
        font-size: 12px;
    }

    .btn-container button{
        height: 45px;
    }
}
</style>