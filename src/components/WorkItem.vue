<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'WorkItem',
    props: {
        name: {
            type: String, 
            default: ''
        },
        description: {
            type: String,
            default: ''
        },
        link: {
            type: String,
            default: '/'
        },
        notClickable: {
            type: Boolean,
            default: false
        },
        inProgress: {
            type: Boolean,
            default: false
        },
        image: {
            type: String,
            default: ''
        },
        whiteImage: {
            type: Boolean,
            default: false
        }
    }
})
</script>

<template>
	<a :class="{work_item_card: true, work_coming_soon: inProgress, work_card_no_click: notClickable}" :href="link">
        <div class="background" :style="{ backgroundImage: `url(${image})` }"></div>
        <div class="work_card_details">
            <div class="work_item_top_section">
                <h2>{{ name }}</h2>
                <span v-if="inProgress" class="coming_soon_badge">Coming Soon</span>
            </div>
            <p>{{ description }}</p>
        </div>
        <div v-if="image != ''" :class="{white_image: whiteImage, work_image_outer: true}">
            <img :src="image" width="65">
        </div>
    </a>
</template>

<style>
.work_item_card{
    min-width: 200px;
    width: fit-content;
    padding: 35px;
    border-radius: 15px;
    background-color: white;
    display: flex;
    flex-direction: row;
    align-items: center;
    gap: 20px;
    overflow-y: hidden;
    text-decoration: none;
    color: black;
    pointer-events: all;
    box-shadow: 0 3px 30px -10px #0004;
}

.work_item_card > .background {
    position: absolute;
    inset: 0;
    display: block;
    background-repeat: no-repeat;
    background-position: 150% 50%;
    background-size: 80%;
    opacity: 0.07;

    display: none;
}

.work_card_details{
    display: flex;
    flex-direction: column;
    gap: 20px;
}

.work_item_top_section{
    display: flex;
    align-items: center;
    flex-wrap: wrap;
    gap: 10px;
}

.coming_soon_badge{
    background-color: black;
    color: white;
    padding: 2px 5px;
    border: 1px solid;
    border-radius: 15px;
    font-size: smaller;
}

.work_coming_soon::before,
.work_coming_soon::after{
    transform: translateZ(0);
    position: absolute;
    content: "";
    width: 100%;
    height: 8px;
    left: 0;
    background: repeating-linear-gradient(-45deg, transparent, transparent 10px, #0004 10px, #0004 20px);
}
.work_coming_soon::before{
    top: 0;
}
.work_coming_soon::after{
    bottom: 0;
}

.work_card_no_click{
    pointer-events: none;
}

.work_image_outer{
    border-radius: 50px;
    padding: 5px;
    width: 80px;
    height: 80px;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
    flex-shrink: 0;
}

.white_image{
    background-color: #2d2d2d;
}
</style>
