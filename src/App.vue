<script setup lang="ts">
//@ts-expect-error: IT IS IMAGE
import image from '/22832983.png';
</script>

<script lang="ts">
import { defineComponent } from 'vue';
import ServiceCard from '@/components/ServiceCard.vue';
import WorkItem from '@/components/WorkItem.vue';
export default defineComponent({
    name: "App",
    components: { ServiceCard, WorkItem }
})
</script>

<template>
    <nav>
        <a href="#works" class="nav_shortcut">works</a>
        <a href="#services" class="nav_shortcut">Services</a>
        <a href="#contact" class="nav_shortcut">Contact</a>
    </nav>
	<main>
        <section id="intro">
            <div class="inner">
                <img :src="image" alt="" width="300" height="300">
                <div class="info_para">
                    <h1>Hi! I'm Zak</h1>
                </div>
            </div>
		</section>
		<section id="works">
            <div class="section_divider">
                <h1>WORKS</h1>
            </div>
            <div class="inner">
            </div>
		</section>
		<section id="services">
            <div class="section_divider">
                <h1>SERVICES</h1>
            </div>
            <div class="inner">
                <div class="services_container">
                    <ServiceCard name="UX Consulting" :rate="70"/>
                    <ServiceCard name="Website Development" :rate="70"/>
                    <ServiceCard name="UX Consulting" :rate="70"/>
                    <ServiceCard name="Website Development" :rate="70"/>
                </div>
            </div>
		</section>
		<section id="contact">
            <div class="section_divider">
                <h1>CONTACT ME</h1>
            </div>
            <div class="inner">

            </div>
		</section>
	</main>
</template>

<style>
@import url('../public/root.css');

#app{
	height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
}

main{
	width: 100%;
	height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    overflow-y: auto;
}

nav{
    position: fixed;
    top: 0px;
    right: 17px;
    width: 100%;
	display: flex;
	justify-content: flex-end;
	text-transform: uppercase;
	padding: var(--top-padding) var(--side-padding);
	font-size: 1.2em;
	gap: 1.5em;
    z-index: 10;
    background-color: white;
}

.nav_shortcut{
	color: var(--text-color);
	text-decoration: none;
	display: flex;
    align-items: flex-end;
}

.nav_shortcut::after{
    content: "";
	background-color: var(--text-color);
    position: absolute;
    height: 2px;
    bottom: 0px;
    left: auto;
    right: 0px;
    width: 0px;
    transition: width 0.6s cubic-bezier(0.2, 1, 0.2, 1) 0s;
}

.nav_shortcut:hover::after{
	left: 0px;
    right: auto;
    width: 100%;
}

main > section{
    width: 100%;
}

main > section > .inner{
    padding: calc(var(--top-padding) * 10) var(--side-padding);
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 50px;
}

.section_divider{
    background-color: white;
    width: 100%;
    height: 10vh;
    min-height: 10vh;
    display: flex;
    align-items: center;
    justify-content: center;
}

/****************************************************************************
************************************ INTRO **********************************
*****************************************************************************/

#intro{
	display: flex;
    gap: 50px;
    padding-top: calc(var(--top-padding) * 2 + 1.3em);
    background-image: linear-gradient(to right, #d2d2ff, #b2eae0);
}

#intro img{
	border-radius: 30px;
}

.info_para{
	min-width: 380px;
	width: calc(100% - 300px - 50px);
	display: flex;
	flex-direction: column;
	gap: 5px;
    color: var(--text-color);
}

/****************************************************************************
********************************* WORKS *************************************
*****************************************************************************/

#works{
    background-image: linear-gradient(to left, #eed2ff, #b2eab5);
}

/****************************************************************************
********************************* SERVICES **********************************
*****************************************************************************/

#services{
    background-image: linear-gradient(to right, #ffd2f2, #e2eab2);
}


#services .services_container{
    width: max(50%, 290px);
}

.services_container > .service_listing:first-of-type{
    border-top: 2px solid black;
}

.services_container > .service_listing:last-of-type{
    border-bottom: 2px solid black;
}

/****************************************************************************
********************************** CONTACT **********************************
*****************************************************************************/

#contact{
    background-image: linear-gradient(to left, #e0d2ff, #b2ddea);
}




@media screen and (max-width: 767px){
	#intro > .inner{
		justify-content: center;
	}
	.info_para{
		width: 100%;
		min-width: 300px;
	}
    nav{
        font-size: 1em;
    }
}


</style>
