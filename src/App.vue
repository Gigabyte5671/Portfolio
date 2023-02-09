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
    <main>
        <nav>
            <a href="#works" class="nav_shortcut">Works</a>
            <a href="#services" class="nav_shortcut">Services</a>
            <a href="#about" class="nav_shortcut">About</a>
        </nav>
        <section id="intro">
            <div class="inner">
                
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
		<section id="about">
            <div class="section_divider">
                <h1>ABOUT</h1>
            </div>
            <div class="inner">
                <div>
                    <img src="/22832983.png" alt="" width="300" height="300" style="border-radius: 150px;">
                    <a href="https://github.com/Gigabyte5671">
                        <img src="/github_logo.svg" alt="Github" width="100">
                    </a>
                    <a href="https://www.linkedin.com/in/zakmanley/">
                        <img src="/linkedin_logo.png" alt="LinkedIn" width="100">
                    </a>
                </div>
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
    position: sticky;
    top: 0;
    left: 0;
    width: 100%;
	display: flex;
	justify-content: flex-end;
	text-transform: uppercase;
	padding: var(--top-padding) var(--side-padding);
	font-size: 1.2em;
	gap: 1.5em;
    z-index: 10;
    background-color: white;
    border-bottom: 1px solid black;
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
    background-image: linear-gradient(to right, #d2d2ff, #b2eae0);
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
********************************** ABOUT **********************************
*****************************************************************************/

#about{
    background-image: linear-gradient(to left, #e0d2ff, #b2ddea);
}

</style>
