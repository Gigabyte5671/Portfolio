<script setup lang="ts">
// @ts-expect-error: Image doesn't have a type definition.
import ProfilePic from './images/Zak-2 - Copy.webp';
</script>

<script lang="ts">
import { defineComponent } from 'vue';
import ServiceCard from '@/components/ServiceCard.vue';
import WorkItem from '@/components/WorkItem.vue';
export default defineComponent({
    name: "App",
    components: { ServiceCard, WorkItem },
    data() {
        return {
            transparentNav: true
        }
    },
    methods: {
        navBackgroundTransition(): void {
            // Observer options.
            const options = {
                root: null,
                rootMargin: '0px',
                threshold: 0
            }

            // Create the observer function.
            const observer = new IntersectionObserver((entries) => {
                entries.forEach((entry) => {
                    if (entry.isIntersecting) {
                        return this.transparentNav = false;
                    }
                    this.transparentNav = true;
                });
            }, options);

            // Bind to the observation target.
            const target = document.querySelector('#works > .inner');
            if (target) {
                observer.observe(target);
            }
        }
    },
    mounted() {
        this.navBackgroundTransition();
    }
})
</script>

<template>
    <nav :class="{ transparent: transparentNav }">
        <ul>
            <li><a href="/" class="title">ZakWeb.dev</a></li>
            <li><a href="#works" class="nav_shortcut"><p>Works</p><span class="material-symbols-rounded">brush</span></a></li>
            <li><a href="#services" class="nav_shortcut"><p>Services</p><span class="material-symbols-rounded">home_repair_service</span></a></li>
            <li><a href="#contact" class="nav_shortcut"><p>Contact</p><span class="material-symbols-rounded">send</span></a></li>
        </ul>
    </nav>
    <main>
        <section id="intro">
            <div class="background">
                <div style="transform: rotate(10deg);">
                    <span class="material-symbols-rounded">auto_awesome</span>
                </div>
                <div style="transform: rotate(50deg);">
                    <span class="material-symbols-rounded">image</span>
                </div>
                <div style="transform: rotate(90deg);">
                    <span class="material-symbols-rounded">movie_filter</span>
                </div>
                <div style="transform: rotate(130deg);">
                    <span class="material-symbols-rounded">send</span>
                </div>
                <div style="transform: rotate(170deg);">
                    <span class="material-symbols-rounded">brush</span>
                </div>
                <div style="transform: rotate(210deg);">
                    <span class="material-symbols-rounded">code</span>
                </div>
                <div style="transform: rotate(250deg);">
                    <span class="material-symbols-rounded">dynamic_form</span>
                </div>
                <div style="transform: rotate(290deg);">
                    <span class="material-symbols-rounded">settings</span>
                </div>
                <div style="transform: rotate(330deg);">
                    <span class="material-symbols-rounded">music_note</span>
                </div>
            </div>
            <div class="inner">
                <img :src="ProfilePic" alt="me" width="400">
                <h1>
                    <span style="animation-delay: 0.0s;">H</span>
                    <span style="animation-delay: 0.05s;">e</span>
                    <span style="animation-delay: 0.1s;">l</span>
                    <span style="animation-delay: 0.15s;">l</span>
                    <span style="animation-delay: 0.2s;">o</span>
                    <span style="animation-delay: 0.25s;">!</span>
                </h1>
                <p>
                    <span style="animation-delay: 0.125s;">W</span>
                    <span style="animation-delay: 0.15s;">e</span>
                    <span style="animation-delay: 0.175s;">l</span>
                    <span style="animation-delay: 0.2s;">c</span>
                    <span style="animation-delay: 0.225s;">o</span>
                    <span style="animation-delay: 0.25s;">m</span>
                    <span style="animation-delay: 0.275s;">e</span>&nbsp;
                    <span style="animation-delay: 0.3s;">t</span>
                    <span style="animation-delay: 0.325s;">o</span>&nbsp;
                    <span style="animation-delay: 0.35s;">m</span>
                    <span style="animation-delay: 0.375s;">y</span>&nbsp;
                    <span style="animation-delay: 0.4s;">p</span>
                    <span style="animation-delay: 0.425s;">o</span>
                    <span style="animation-delay: 0.45s;">r</span>
                    <span style="animation-delay: 0.475s;">t</span>
                    <span style="animation-delay: 0.5s;">f</span>
                    <span style="animation-delay: 0.525s;">o</span>
                    <span style="animation-delay: 0.55s;">l</span>
                    <span style="animation-delay: 0.575s;">i</span>
                    <span style="animation-delay: 0.6s;">o</span>
                </p>
            </div>
		</section>
		<section id="works">
            <div class="section_divider">
                <h1>WORKS</h1>
            </div>
            <div class="inner">
                <WorkItem name="DashBooks Website" description="A website for an upcoming project." link="https://dashbooks.app/" image="https://dashbooks.app/assets/logo.aa87dd82.svg" :inProgress="true"/>

                <WorkItem name="DashBooks" description="Bookkeeping, made fast. A web application for time keeping, invoicing and finances." link="https://demo.dashbooks.app/" image="https://dashbooks.app/assets/logo.aa87dd82.svg" :inProgress="true"/>

                <WorkItem name="Vircadia Web App" description="Your open source portal to the metaverse!" link="https://app.vircadia.com/" image="https://raw.githubusercontent.com/vircadia/vircadia-web/master/public/assets/vircadia-icon.svg"/>

                <WorkItem name="CSS Canvas" description="Create amazing CSS components, without any markup!" link="https://gigabyte5671.github.io/CSS-Canvas/" image="https://gigabyte5671.github.io/CSS-Canvas/assets/logo-small.3797bbd8.webp"/>

                <WorkItem name="Micro Test-Runner" description="A minimal JavaScript test runner." link="https://www.npmjs.com/package/micro-test-runner" image="https://fonts.gstatic.com/s/i/short-term/release/materialsymbolsoutlined/javascript/default/48px.svg"/>
                
                <WorkItem name="Auto Type" description="A simple auto-typing/typewriter effect written in vanilla JS." link="https://gigabyte5671.github.io/AutoType/" image="https://gigabyte5671.github.io/AutoType/favicon.svg" :whiteImage="true"/>

                <WorkItem name="DOM Particles" description="A simple particle engine that uses vanilla JavaScript to run within the native HTML DOM." link="https://gigabyte5671.github.io/DOM-Particles/" image="https://gigabyte5671.github.io/DOM-Particles/favicon.webp"/>

                <WorkItem name="Wilderzone API" description="A Node JS API to retreive and return the current number of players in the Tribes Ascend game." link="https://api.wilderzone.live/" image="https://raw.githubusercontent.com/wilderzone/ta-network-api/main/logo.svg"/>

                <WorkItem name="Wilderzone Live" description="The hub for all things Tribes: Ascend." link="https://wilderzone.live/" image="https://raw.githubusercontent.com/wilderzone/wilderzone-live/vue/src/assets/branding/Logo-Light.svg"/>

                <WorkItem name="Wilderzone Org" description="Base repo for the Tribes Ascend Community Hub's Wilderzone.org restoration project." link="https://wilderzone.org/" image="https://github.com/wilderzone/wilderzone-live/blob/main/assets/images/wilderzone_logo_symbol_black_small.png?raw=true" :inProgress="true"/>

                <WorkItem name="Cookie Manager" description="An incredibly simple and lightweight library for adding, fetching, modifying, and removing browser cookies." link="https://gigabyte5671.github.io/CookieManager/" image="https://img.icons8.com/color/96/000000/cookies.png"/>
            </div>
		</section>
		<section id="services">
            <div class="section_divider">
                <h1>SERVICES</h1>
            </div>
            <div class="inner">
                <div class="services_container">
                    <ServiceCard name="UX Consulting" :rate="90"/>
                    <ServiceCard name="Website Development" :rate="70"/>
                </div>
            </div>
		</section>
		<section id="contact">
            <div class="section_divider">
                <h1>CONTACT</h1>
            </div>
            <div class="inner">
                <a href="mailto:contact@zakweb.dev" class="email"><span class="material-symbols-rounded">email</span>&nbsp;&nbsp;&nbsp;contact@zakweb.dev</a>
                <div class="links">
                    <a href="https://github.com/Gigabyte5671">
                        <img src="https://cdn.simpleicons.org/github/#181717" alt="Github" width="100">
                    </a>
                    <a href="https://www.linkedin.com/in/zakmanley/">
                        <img src="https://cdn.simpleicons.org/linkedin/#0A66C2" alt="LinkedIn" width="100">
                    </a>
                    <a href="https://www.npmjs.com/~gigabyte5671">
                        <img src="https://cdn.simpleicons.org/npm/#CB3837" alt="NPM" width="100">
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
	padding: 0.3rem 2ch;
    z-index: 10;
    background-color: white;
    box-shadow: 0 0 20px -4px #0004;
    transition: 0.2s ease background-color, 0.2s ease box-shadow;
}

nav.transparent{
    background-color: transparent;
    box-shadow: 0 0 20px -4px #0000;
}

nav .title{
    opacity: 1;
}

nav.transparent .title{
    opacity: 0;
}

nav > ul{
	display: flex;
    flex-flow: row nowrap;
	justify-content: flex-end;
	gap: 3ch;
    width: 100%;
    padding: 0;
    list-style: none;
	text-transform: uppercase;
}

nav > ul li:first-child{
    margin-right: auto;
	text-transform: none;
}

nav > ul li a{
	color: var(--text-color);
    text-decoration: none;
}

.nav_shortcut,
.email{
	display: flex;
    align-items: flex-end;
}

.nav_shortcut::after,
.email::after{
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

.nav_shortcut:hover::after,
.email:hover::after{
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
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 10vh;
    min-height: 10vh;
    background-color: white;
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
    overflow: hidden;
}

#intro > .background{
    position: absolute;
    inset: 0;
    z-index: 1;
    display: flex;
    justify-content: center;
    align-items: center;
    transform-origin: center;
    animation: introBackgroundRotate 150s linear infinite;
    user-select: none;
}

@keyframes introBackgroundRotate {
    0%   {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(360deg);
    }
}

#intro > .background > div{
    position: absolute;
    display: flex;
    flex-flow: row nowrap;
    justify-content: flex-start;
    align-items: center;
    width: 0;
    transform-origin: center;
    opacity: 0;
    animation: introIconsTransitionIn 0.75s 0.5s ease forwards;
}

@keyframes introIconsTransitionIn {
    0%   {
        width: 0;
        opacity: 0;
    }
    100% {
        width: 95vmin;
        opacity: 1;
    }
}

#intro > .background > div span{
    position: absolute;
    color: #fffb;
    /* color: #f116; */
    font-size: clamp(48px, 6vmax, 5rem);
    text-shadow: 0px 0px 0.5em #fff8;
    transform-origin: center;
    transition: 0.1s ease color;
    animation: introIconsRotate 150s linear infinite;
}

@keyframes introIconsRotate {
    0%   {
        transform: rotate(0deg);
    }
    100% {
        transform: rotate(-360deg);
    }
}

#intro > .background > div:nth-child(2) span{
    filter: hue-rotate(19deg) brightness(1.2);
}
#intro > .background > div:nth-child(3) span{
    filter: hue-rotate(110deg);
}
#intro > .background > div:nth-child(4) span{
    filter: hue-rotate(146deg);
}
#intro > .background > div:nth-child(5) span{
    filter: hue-rotate(180deg);
}
#intro > .background > div:nth-child(6) span{
    filter: hue-rotate(216deg);
}
#intro > .background > div:nth-child(7) span{
    filter: hue-rotate(252deg);
}
#intro > .background > div:nth-child(8) span{
    filter: hue-rotate(288deg);
}
#intro > .background > div:nth-child(9) span{
    filter: hue-rotate(324deg);
}

#intro > .inner{
    z-index: 2;
    display: flex;
    flex-flow: column wrap;
    justify-content: center;
    align-items: center;
    gap: 0.5rem;
    filter: drop-shadow(0px 0px 180px #fff);
}

#intro img{
    width: min(400px, 75vw);
    border-radius: 50%;
    mask-image: radial-gradient(circle at center, black 62%, transparent);
    -webkit-mask-image: radial-gradient(circle at center, black 62%, transparent);
    opacity: 0;
    animation: introImageTransitionIn 1s ease forwards;
}

@keyframes introImageTransitionIn {
    0%   {
        opacity: 0;
    }
    100% {
        opacity: 1;
    }
}

#intro h1{
    font-size: 5em;
    overflow: hidden;
    mask-image: linear-gradient(180deg, black 75%, transparent);
    -webkit-mask-image: linear-gradient(180deg, black 75%, transparent);
}

#intro h1 span{
    display: inline-block;
    transform: translateY(100%);
    opacity: 0;
    animation: introHelloTransitionIn 0.5s ease forwards;
}

#intro p{
    font-size: large;
    line-height: 2;
    overflow: hidden;
    mask-image: linear-gradient(180deg, black 95%, transparent);
    -webkit-mask-image: linear-gradient(180deg, black 95%, transparent);
}

#intro p span{
    display: inline-block;
    transform: translateY(100%);
    opacity: 0;
    animation: introHelloTransitionIn 0.5s ease forwards;
}

@keyframes introHelloTransitionIn {
    0%   {
        transform: translateY(100%);
        opacity: 0;
    }
    100% {
        transform: translateY(0%);
        opacity: 1;
    }
}

@media screen and (max-width: 900px) {
    #intro > .background{
        display: none;
    }
}
@media screen and (max-height: 900px) {
    #intro > .background{
        display: none;
    }
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

#contact > .inner {
    display: flex;
    flex-flow: column nowrap;
}

#contact .email {
    width: max-content;
    margin: auto;
    padding: 1ch 2ch;
    color: var(--text-color);
    text-align: center;
    text-decoration: none;
    background-color: #fff;
    border-radius: 10px;
    box-shadow: 0 3px 30px -10px #0004;
    overflow: hidden;
}

#contact .links {
    display: flex;
    flex-flow: row wrap;
    gap: 5rem;
    margin: auto;
}


@media screen and (max-width: 600px) {
    .nav_shortcut > p{
        display: none;
    }
    .nav_shortcut > span{
        display: contents;
    }
    h2 {
        font-size: 1.3rem;
    }

}

</style>
