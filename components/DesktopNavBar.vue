<template>
    <div class="nav-bar-container">
        <div class="name-container">
            <a class="big-name" href="/#intro">Dan Becker</a>
        </div>
        <div class="items-container">
            <div class="nav-bar-item email-link" @click="handleEmailClick">
                <span>{{emailText}}</span>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from 'vue'

const emailText = ref("daniel.becker000@gmail.com")

const copyToClipboard = (callback) => {
    navigator.clipboard.writeText('daniel.becker000@gmail.com').then(callback)
}

const handleEmailClick = () => {
        copyToClipboard(() => {
        console.log('handle email click used    ')
        emailText.value = 'email copied to clipboard ✓'
    })
}

</script>

<style lang="scss" scoped>
.nav-bar-container{ 
    border-bottom: 1px solid red;
    backdrop-filter: blur(3px);
    font-family: $dot-gothic;
    display: flex;
    justify-content: space-between;
    align-items: center;
        a {
            text-decoration: none;  
            color: unset;
        }
    
    .name-container {
        display: flex;
        justify-content: center;
        align-items: center;
        text-align: center;
       
        .big-name{
            color: white;
            font-size: 4.5rem;
            margin: 2rem;
            &:hover {
            color: greenyellow;
        }
        }
    }
    .items-container{
        display: flex; 
        
        .nav-bar-item {
            display: flex;
            justify-content: center;
            align-items: center;
            padding: 2rem;
            text-align: center;
            font-size: 1.6rem;
            overflow: hidden;
            &:hover {
                color: yellow;
            }

           
            &.email-link {
                display: flex;
                flex-direction: column;
            }
        }  
    }
    
}

</style>