<script setup>
import { ref, watch, defineEmits } from "vue"

const emit = defineEmits(['emailInput']);

const email = ref("")
const emailError = ref('');
const isValidated = ref(true)
watch(email, () => {
    console.log(email.value)
})

const validateEmail = () => {
    const emailRegex = /^[a-zA-Z0-9._-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,4}$/;
    if (!emailRegex.test(email.value)) {
        emailError.value = 'Valid email required';
        isValidated.value = false
        console.log(emailError.value)
    } else {
        emailError.value = '';
        console.log('Valid email🎉😍')
        isValidated.value = true
    }
}

const getErrorStyle = () => {
    if (!isValidated.value) {
        return {
            fontFamily: '\'Roboto\', sans-serif',
            fontWeight: 700,
            color: 'hsl(4, 100%, 67%)',
        }
    }
}

const getStyle = () => {
    if (!isValidated.value) {
        return {
            border: '1px solid hsl(4, 100%, 67%)',
            backgroundColor: 'hsla(4, 100%, 67%, 0.1)',
            color: 'hsl(4, 100%, 67%)'
        }
    }
}

const onSubmit = () => {
    if (isValidated.value && email.value != "") {
        emit('emailInput', email.value);
        console.log('Submitted')
    }
 
};

</script>

<template>
    <main>
        <div class="container">
            <div class="img-container">
            </div>
            <div class="main-body">
                <div class="tag">
                    <h1 class="tagline">Stay updated!</h1>
                    <p class="tag-description">Join 60,000+ product managers receiving monthly updates on:</p>
                </div>
                <div class="perks">
                    <div class="perk">
                        <img src="../assets/images/icon-list.svg" alt="">
                        <p>Product discovery and building what matters</p>
                    </div>
                    <div class="perk">
                        <img src="../assets/images/icon-list.svg" alt="">
                        <p>Measuring to ensure updates are a success</p>
                    </div>
                    <div class="perk">
                        <img src="../assets/images/icon-list.svg" alt="">
                        <p>And much more!</p>
                    </div>
                </div>
                <div class="input-tags">
                    <p class="input-label">Email address</p>
                    <p :style="getErrorStyle()" class="error-message">{{ emailError }}</p>
                </div>
                <input type="email" placeholder="email@company.com" v-model="email" @input="validateEmail"
                    :style="getStyle()">
                <button id="submit" @click="onSubmit()">Subscribe to monthly newsletter</button>
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
    width: 100%;
    display: flex;
    align-items: start;
    justify-content: center;
}

.container {
    width: 100%;
    background-color: hsl(0, 0%, 100%);
}

.img-container {
    height: 280px;
    width: 100%;
    border-bottom-left-radius: 15px;
    border-bottom-right-radius: 15px;
    overflow: hidden;
    background-image: url(../assets/images/illustration-sign-up-mobile.svg);
    background-repeat: no-repeat;
    background-size: cover;
}

.main-body {
    padding: 0px 20px 0px 20px;
}

.tagline {
    font-family: 'Roboto', sans-serif;
    color: hsl(234, 29%, 20%);
    font-weight: 700;
    font-size: 40px;
    margin-top: 30px;
    margin-bottom: 20px;
    line-height: 1;
}

.tag-description {
    font-family: 'Roboto', sans-serif;
    font-weight: 400;
    color: hsl(234, 29%, 20%);
    font-size: 16px;
    margin-bottom: 30px;
}

.perks {
    width: 100%;
    display: flex;
    flex-direction: column;
    align-items: start;
    margin-bottom: 20px;
}

.perk {
    display: flex;
    align-items: start;
    justify-content: start;
    margin-bottom: 10px;
}

.perk img {
    margin-right: 10px;
}

.perk p {
    font-family: 'Roboto', sans-serif;
    font-weight: 400;
    color: hsl(234, 29%, 20%);
    font-size: 16px;
}

.input-tags {
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.input-label {
    font-family: 'Roboto', sans-serif;
    font-weight: 700;
    color: hsl(234, 29%, 20%);
    margin-bottom: 3px;
}

input {
    width: 100%;
    height: 58px;
    border: 0.5px solid hsl(231, 7%, 60%);
    border-radius: 10px;
    font-family: 'Roboto', sans-serif;
    font-weight: 400;
    font-size: 16px;
    color: hsl(234, 29%, 20%);
    padding-left: 15px;
    margin-bottom: 30px;
    transition: all 0.2s ease-in;
}

input::placeholder {
    color: hsl(231, 7%, 60%);
}

input:focus {
    outline: none;
    border: 2px solid hsl(231, 7%, 60%);
}


#submit {
    width: 100%;
    height: 58px;
    background-color: hsl(234, 29%, 20%);
    border: none;
    border-radius: 10px;
    font-family: 'Roboto', sans-serif;
    font-weight: 700;
    font-size: 16px;
    color: hsl(0, 0%, 100%);
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 20px;
    transition: all 0.3s ease-in-out;
}

#submit:hover {
    background: linear-gradient(to right, #ff5379, #ff6257, #ff693e);
    cursor: pointer;
}

@media only screen and (min-width: 768px) {
    main {
        align-items: center;
        background-color: hsl(235, 18%, 26%);
    }

    .container {
        height: 500px;
        width: 700px;
        display: flex;
        flex-direction: row-reverse;
        align-items: center;
        border-radius: 20px;
        padding: 20px;
    }

    .img-container {
        width: 45%;
        height: 100%;
        background-image: url(../assets/images/illustration-sign-up-desktop.svg);
        background-size: cover;
        background-position: center;
        border-radius: 15px;
    }

    .main-body {
        width: 55%;
        padding-right: 40px;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    .tagline {
        font-size: 30px;
        line-height: 1;
        margin-bottom: 10px;
    }

    .tag-description {
        font-size: 12px;
        margin-bottom: 10px;
    }

    .perks {
        margin-bottom: 10px;
    }

    .perk p {
        font-size: 12px;
    }

    .input-label {
        font-size: 12px;
    }

    .error-message {
        font-size: 12px;
    }

    input {
        height: 45px;
        border-radius: 6px;
        font-size: 12px;
        margin-bottom: 15px;
    }

    #submit {
        height: 45px;
        border-radius: 6px;
        font-size: 12px;
        margin-bottom: 0px;
    }
}
</style>