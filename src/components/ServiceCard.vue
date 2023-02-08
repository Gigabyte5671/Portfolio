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
        <p class="soft_text">STARTING AT</p>
        <p class="bold_text"> ${{ rate }} / {{ ratePerUnit }}</p>
    </div>
</template>

<style scoped>
.service_listing{
    border-top: 1px solid black;
    border-bottom: 1px solid black;
    width: 100%;
    padding: 2vh 0px;
}

p{
    text-transform: uppercase;
}

.bold_text{
    font-weight: 700;
}

.soft_text{
    opacity: 0.7;
}
</style>
