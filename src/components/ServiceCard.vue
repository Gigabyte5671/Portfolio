<script lang="ts">
import { defineComponent } from 'vue';
export default defineComponent({
    name: 'ServiceCard',
    props: {
        name: {
            type: String,
            default: ''
        },
        rate: {
            type: Number,
            default: 0
        },
        ratePerUnit: {
            type: String,
            default: 'HOUR'
        }
    }
})
</script>

<template>
	<div class="service_listing">
        <h2>{{ name }}</h2>
        <p class="soft_text">Starting At</p>
        <p class="bold_text"> ${{ rate }} / {{ ratePerUnit }}</p>
        <slot></slot>
    </div>
</template>

<style scoped>
.service_listing{
    width: 100%;
    padding: 1rem 1.5rem 2rem;
    background-color: white;
    border-radius: 10px;
    box-shadow: 0 3px 30px -10px #0004;
}

.bold_text{
    font-weight: 700;
}

.soft_text{
    opacity: 0.7;
}
</style>
