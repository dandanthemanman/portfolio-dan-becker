<template>
    <div class="nav-bar-container"  >
        <div class="name-container" :style="blurStyling">
            <p class="big-name">Dan Becker</p>
            <p class="little-name">web development</p>
        </div>
        <div class="items-container">
            <BurgerMenu/>
        </div>
    </div>
</template>

<script setup>
import { store } from "../store/store"
import { ref, computed } from 'vue'
import BurgerMenu from '@/components/BurgerMenu.vue'

const blurStyling = computed(() => {
    return {
        "filter": store.siteBlur ? "blur(4px)" : ""
    }
})


const emailText = ref("Email me")

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
        flex-direction: column;
       margin: 2rem;
        .big-name{
            margin: unset;
            color: white;
            font-size: 4.5rem;
            @media (min-width: $breakpoint-md) {
                font-size: 6rem;
            }
        }
        .little-name {
            margin: unset;
            color: white;
            font-size: 2rem;
            @media (min-width: $breakpoint-md) {
                font-size: 3.5rem;
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
                .copy-to-clipboard-text {
                    transform: translateY(calc(200%));  
                }
                &:hover {
                    span {
                        transform: translateY(calc(-200% - 0.5rem));  
                        transition: transform 0.3s cubic-bezier(0.45, 0, 0.55, 1);
                    }
                }     
            }
        }  
    }
    
}

</style>