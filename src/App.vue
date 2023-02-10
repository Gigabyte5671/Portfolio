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
        <a href="#works" class="nav_shortcut"><p>Works</p><span class="material-symbols-rounded">brush</span></a>
        <a href="#services" class="nav_shortcut"><p>Services</p><span class="material-symbols-rounded">home_repair_service</span></a>
        <a href="#contact" class="nav_shortcut"><p>Contact</p><span class="material-symbols-rounded">send</span></a>
    </nav>
    <main>
        <section id="intro">
            <div class="inner">
                
            </div>
		</section>
		<section id="works">
            <div class="section_divider">
                <h1>WORKS</h1>
            </div>
            <div class="inner">
                <WorkItem name="DashBooks Website" description="A website for an upcoming project" link="https://dashbooks.app/" image="https://dashbooks.app/assets/logo.aa87dd82.svg" :inProgress="true"/>

                <WorkItem name="CSS Canvas" description="Create amazing CSS components, without any markup!" link="https://gigabyte5671.github.io/CSS-Canvas/" image="https://gigabyte5671.github.io/CSS-Canvas/assets/logo-small.3797bbd8.webp"/>

                <WorkItem name="Variable Listener" description="Variable Listener is a library enabling client-side JavaScript to execute arbitrary functions when the value of any global variable changes." link="https://github.com/Gigabyte5671/VariableListener"/>
                
                <WorkItem name="Auto Type" description="A simple auto-typing/typewriter effect written in vanilla JS." link="https://gigabyte5671.github.io/AutoType/" image="https://gigabyte5671.github.io/AutoType/favicon.svg" :whiteImage="true"/>

                <WorkItem name="DOM Particles" description="A simple particle engine that uses vanilla JavaScript to run within the native HTML DOM." link="https://gigabyte5671.github.io/DOM-Particles/" image="https://gigabyte5671.github.io/DOM-Particles/favicon.webp"/>

                <WorkItem name="Wilderzone API" description="A Node JS API to retreive and return the current number of players in the Tribes Ascend game." link="https://api.wilderzone.live/" image="https://raw.githubusercontent.com/wilderzone/ta-network-api/main/logo.svg"/>
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
                <h1>CONTACT</h1>
            </div>
            <div class="inner">
                <div>
                    <img src="/22832983.png" alt="" width="300" height="300" style="border-radius: 150px;">
                    <p>Email: contact@zakweb.dev</p>
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
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@400&display=swap');

:root {
	--top-padding: 1vh;
	--side-padding: 1rem;
    --text-color: #000;
}

*,
*::before,
*::after {
	position: relative;
	box-sizing: border-box;
	margin: 0;
	font-weight: normal;
}

html {
    font-family: 'Manrope', 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
    scroll-behavior: smooth;
    scroll-padding-top: calc(0.6rem + 1rem);
	background-repeat: no-repeat;
	height: 100%;
}

body {
    margin: 0px;
    height: 100%;
    overflow-x: hidden;
}

main{
	width: 100%;
	height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
}

nav{
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
	display: flex;
	justify-content: flex-end;
	text-transform: uppercase;
	padding: 0.3rem 2ch;
	gap: 1.5em;
    z-index: 10;
    background-color: white;
    box-shadow: 0 0 20px -4px #0004;
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

.nav_shortcut > span{
    display: none;
}

/****************************************************************************
************************************ INTRO **********************************
*****************************************************************************/

#intro{
	display: flex;
    justify-content: center;
    align-items: center;
    gap: 50px;
    background-image: linear-gradient(#BDF3FF, #BDD2FF);
    min-height: 100%;
    height: 100%;
}

/****************************************************************************
********************************* WORKS *************************************
*****************************************************************************/
#works{
    background-image: linear-gradient(#BDBDFF, #DEBDFF);
}

/****************************************************************************
********************************* SERVICES **********************************
*****************************************************************************/

#services{
    background-image: linear-gradient(#CCFFBD, #BDFFCF);
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
    background-image: linear-gradient(#E9FFBD, #FFDDBD);
}


@media screen and (max-width: 600px) {
    .nav_shortcut > p{
        display: none;
    }
    .nav_shortcut > span{
        display: contents;
    }

}

</style>
