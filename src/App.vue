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
	components: {
		ServiceCard,
		WorkItem
	},
	data() {
		return {
			transparentNav: true,
			landingIcons: [
				'auto_awesome',
				'image',
				'movie_filter',
				'send',
				'brush',
				'code',
				'dynamic_form',
				'settings',
				'music_note'
			]
		};
	},
	methods: {
		initNavScrollTransition(): void {
			// Observer options.
			const options = {
				root: null,
				rootMargin: '0px',
				threshold: 0
			};

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
		this.initNavScrollTransition();
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
				<div v-for="(icon, index) of landingIcons" :style="{ transform: `rotate(${(360 / landingIcons.length) * index + 10}deg)` }">
					<span class="material-symbols-rounded">{{ icon }}</span>
				</div>
			</div>
			<div class="inner">
				<img :src="ProfilePic" alt="me" width="400">
				<h1 style="opacity: 0.6;">
					<span v-for="(character, index) of 'Hello!'" :style="{ animationDelay: `${0.05 * index}s` }">{{ character }}</span>
				</h1>
			</div>
		</section>

		<section id="works">
			<div class="section_divider">
				<h1>WORKS</h1>
			</div>
			<div class="inner">
				<WorkItem
					name="DashBooks Website"
					description="A website for an upcoming project."
					link="https://dashbooks.app/"
					image="https://dashbooks.app/assets/logo.aa87dd82.svg"
					:badges="['Vue.js', 'Vite', 'TypeScript', 'Google_Domains']"
					inProgress
				/>
				<WorkItem
					name="DashBooks"
					description="Bookkeeping, made fast. A web application for time keeping, invoicing and finances."
					link="https://demo.dashbooks.app/"
					image="https://dashbooks.app/assets/logo.aa87dd82.svg"
					:badges="['Vue.js', 'Webpack', 'TypeScript', 'Firebase', 'GitHub_Actions', 'Google_Domains']"
					inProgress
				/>
				<WorkItem
					name="Vircadia Web App"
					description="Your open source portal to the metaverse!"
					link="https://app.vircadia.com/"
					image="https://raw.githubusercontent.com/vircadia/vircadia-web/master/public/assets/vircadia-icon.svg"
					:badges="['Vue.js', 'Webpack', 'TypeScript', 'GitHub_Actions']"
				/>
				<WorkItem
					name="CSS Canvas"
					description="Create amazing CSS components, without any markup!"
					link="https://css-canvas.zakweb.dev/"
					image="https://css-canvas.zakweb.dev/assets/logo-small.3797bbd8.webp"
					:badges="['Vue.js', 'Vite', 'TypeScript', 'GitHub_Actions']"
				/>
				<WorkItem
					name="Micro Test-Runner"
					description="A minimal JavaScript test runner."
					link="https://www.npmjs.com/package/micro-test-runner"
					image="https://fonts.gstatic.com/s/i/short-term/release/materialsymbolsoutlined/javascript/default/48px.svg"
					:badges="['TypeScript', 'NPM']"
				/>
				<WorkItem
					name="Auto Type"
					description="A simple auto-typing/typewriter effect written in vanilla JS."
					link="https://autotype.zakweb.dev/"
					image="https://autotype.zakweb.dev/favicon.svg"
					:badges="['CSS_3', 'TypeScript', 'Firebase']"
					whiteImage
				/>
				<WorkItem
					name="DOM Particles"
					description="A simple particle engine that uses vanilla JavaScript to run within the native HTML DOM."
					link="https://dom-particles.zakweb.dev/"
					image="https://dom-particles.zakweb.dev/favicon.webp"
					:badges="['HTML_5', 'JavaScript']"
				/>
				<WorkItem
					name="Wilderzone API"
					description="Web interface for easy access to the TA Network API."
					link="https://api.wilderzone.live/"
					image="https://raw.githubusercontent.com/wilderzone/ta-network-api/main/logo.svg"
					:badges="['TypeScript', 'Firebase', 'Express', 'Google_Domains']"
				/>
				<WorkItem
					name="TA Network API"
					description="An open interface for fetching data from the Tribes: Ascend servers."
					link="https://www.npmjs.com/package/ta-network-api"
					image="https://raw.githubusercontent.com/wilderzone/ta-network-api/main/logo.svg"
					:badges="['TypeScript', 'NPM']"
				/>
				<WorkItem
					name="Wilderzone Live"
					description="The hub for all things Tribes: Ascend."
					link="https://wilderzone.live/"
					image="https://raw.githubusercontent.com/wilderzone/wilderzone-live/vue/src/assets/branding/Logo-Light.svg"
					:badges="['HTML_5', 'CSS_3', 'JavaScript', 'GitHub_Pages', 'Google_Analytics', 'Google_Domains']"
				/>
				<WorkItem
					name="Wilderzone Org"
					description="Base repo for the Tribes Ascend Community Hub's Wilderzone.org restoration project."
					link="https://wilderzone.org/"
					image="https://github.com/wilderzone/wilderzone-live/blob/main/assets/images/wilderzone_logo_symbol_black_small.png?raw=true" 
					:badges="['HTML_5', 'CSS_3', 'GitHub_Pages', 'Google_Domains']"
					inProgress
				/>
				<WorkItem
					name="Cookie Manager"
					description="An incredibly simple and lightweight library for adding, fetching, modifying, and removing browser cookies."
					link="https://cookie-manager.zakweb.dev/"
					image="https://img.icons8.com/color/96/000000/cookies.png"
					:badges="['JavaScript']"
				/>
			</div>
		</section>

		<section id="services">
			<div class="section_divider">
				<h1>SERVICES</h1>
			</div>
			<div class="inner">
				<div class="services_container">
					<ServiceCard name="UX Consulting" :rate="90">
						<br>
						<p>One-off or regular consulting sessions to help you improve the user experience of your application, game, or website. We can discuss directly over your preferred communication medium, or communicate back and forth via email. </p>
						<br>
						<p>Deliverables:</p>
						<br>
						<ul>
							<li><b>Tips & Advice</b><br>Tips and advice on how you can improve the user experience (UX) of your application, game, or website.</li>
							<li><b>Guides</b><br>A direct explanation of features you can improve, and clear guidance on how to implement fixes.</li>
						</ul>
					</ServiceCard>
					<br>
					<br>
					<ServiceCard name="Website Development" :rate="70">
						<br>
						<p>Deliverables:</p>
						<br>
						<ul>
							<li><b>Project Discussion Meeting</b><br>A meeting over your preferred communication medium to discuss the project goals and website requirements.</li>
							<li><b>Design Mockup</b><br>An initial mockup of the website's design, so you can give feedback and make adjustments before development starts.</li>
							<li><b>First Development Draft</b><br>Hot off the press! The first draft of the website with basic functionality in place.</li>
							<li><b>Services Discussion Meeting</b><br>A meeting over your preferred communication medium to discuss any third-party services that are required to complete the functionality of your website. For example: domains, hosting, databases, etc.</li>
							<li><b>Complete Website</b><br>The keys to the Kingdom! Your new, fully-functional website will be handed over, along with any tools and documentation you need to keep it running.</li>
						</ul>
					</ServiceCard>
				</div>
			</div>
		</section>

		<section id="contact">
			<div class="section_divider">
				<h1>CONTACT</h1>
			</div>
			<div class="inner">
				<a href="mailto:contact@zakweb.dev" class="email"><span class="material-symbols-rounded">email</span>&nbsp;&nbsp;&nbsp;contact@zakweb.dev</a>
				<a href="https://discordapp.com/users/210305632266485760" class="email"><img src="https://cdn.simpleicons.org/discord/" alt="Discord" width="25">&nbsp;&nbsp;&nbsp;Gigabyte#3310</a>
				<div class="links">
					<a href="https://github.com/Gigabyte5671">
						<img src="https://cdn.simpleicons.org/github/#181717" alt="Github" width="60">
					</a>
					<a href="https://www.linkedin.com/in/zakmanley/">
						<img src="https://cdn.simpleicons.org/linkedin/#0A66C2" alt="LinkedIn" width="60">
					</a>
					<a href="https://www.npmjs.com/~gigabyte5671">
						<img src="https://cdn.simpleicons.org/npm/#CB3837" alt="NPM" width="60">
					</a>
				</div>
			</div>
		</section>
	</main>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Manrope:wght@400&display=swap');

:root {
	--text-color: #000;
	--background-color: #fff;
}

*,
*::before,
*::after {
	position: relative;
	box-sizing: border-box;
	margin: 0;
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

main {
	width: 100%;
	height: 100%;
	display: flex;
	flex-direction: column;
	justify-content: flex-start;
}

h1,
h2,
h3 {
	font-weight: normal;
}

nav {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	display: flex;
	padding: 0.3rem 2ch;
	z-index: 10;
	background-color: var(--background-color);
	box-shadow: 0 0 20px -4px #0004;
	transition: 0.2s ease background-color, 0.2s ease box-shadow;
}
nav.transparent {
	background-color: transparent;
	box-shadow: 0 0 20px -4px #0000;
}

nav .title {
	opacity: 1;
}
nav.transparent .title {
	opacity: 0;
}

nav > ul {
	display: flex;
	flex-flow: row nowrap;
	justify-content: flex-end;
	gap: 3ch;
	width: 100%;
	padding: 0;
	list-style: none;
	text-transform: uppercase;
}

nav > ul li:first-child {
	margin-right: auto;
	text-transform: none;
}

nav > ul li a {
	color: var(--text-color);
	text-decoration: none;
}

.nav_shortcut,
.email {
	display: flex;
	align-items: flex-end;
}

.nav_shortcut::after,
.email::after {
	content: '';
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
.email:hover::after {
	left: 0px;
	right: auto;
	width: 100%;
}

main > section {
	width: 100%;
}

main > section > .inner {
	padding: 10vh 1rem;
	display: flex;
	flex-wrap: wrap;
	justify-content: center;
	gap: 50px;
}

.section_divider {
	display: flex;
	align-items: center;
	justify-content: center;
	width: 100%;
	height: 10vh;
	min-height: 10vh;
	background-color: var(--background-color);
}

.nav_shortcut > span {
	display: none;
}

@media screen and (max-width: 600px) {
	.nav_shortcut > p {
		display: none;
	}
	.nav_shortcut > span {
		display: contents;
	}
	h2 {
		font-size: 1.3rem;
	}
}

/****************************************************************************
************************************ INTRO **********************************
*****************************************************************************/

#intro {
	display: flex;
	justify-content: center;
	align-items: center;
	gap: 50px;
	background-image: linear-gradient(#BDF3FF, #BDD2FF);
	min-height: 100%;
	height: 100%;
	overflow: hidden;
}

#intro > .background {
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

#intro > .background > div {
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

#intro > .background > div span {
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

#intro > .background > div:nth-child(2) span {
	filter: hue-rotate(19deg) brightness(1.2);
}
#intro > .background > div:nth-child(3) span {
	filter: hue-rotate(110deg);
}
#intro > .background > div:nth-child(4) span {
	filter: hue-rotate(146deg);
}
#intro > .background > div:nth-child(5) span {
	filter: hue-rotate(180deg);
}
#intro > .background > div:nth-child(6) span {
	filter: hue-rotate(216deg);
}
#intro > .background > div:nth-child(7) span {
	filter: hue-rotate(252deg);
}
#intro > .background > div:nth-child(8) span {
	filter: hue-rotate(288deg);
}
#intro > .background > div:nth-child(9) span {
	filter: hue-rotate(324deg);
}

#intro > .inner {
	z-index: 2;
	display: flex;
	flex-flow: column wrap;
	justify-content: center;
	align-items: center;
	gap: 0.5rem;
	filter: drop-shadow(0px 0px 180px #fff);
}

#intro img {
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

#intro h1 {
	font-size: 5em;
	overflow: hidden;
	mask-image: linear-gradient(180deg, black 75%, transparent);
	-webkit-mask-image: linear-gradient(180deg, black 75%, transparent);
}

#intro h1 span {
	display: inline-block;
	transform: translateY(100%);
	opacity: 0;
	animation: introHelloTransitionIn 0.5s ease forwards;
}

#intro p {
	font-size: large;
	line-height: 2;
	overflow: hidden;
	mask-image: linear-gradient(180deg, black 95%, transparent);
	-webkit-mask-image: linear-gradient(180deg, black 95%, transparent);
}

#intro p span {
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
	#intro > .background {
		display: none;
	}
}
@media screen and (max-height: 900px) {
	#intro > .background {
		display: none;
	}
}

/****************************************************************************
********************************* WORKS *************************************
*****************************************************************************/
#works {
	background-image: linear-gradient(#BDBDFF, #DEBDFF);
}

/****************************************************************************
********************************* SERVICES **********************************
*****************************************************************************/

#services {
	background-image: linear-gradient(#CCFFBD, #BDFFCF);
}

#services .services_container {
	width: 100%;
	max-width: 800px;
}

/****************************************************************************
********************************** CONTACT **********************************
*****************************************************************************/
#contact {
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
	background-color: var(--background-color);
	border-radius: 10px;
	box-shadow: 0 3px 30px -10px #0004;
	overflow: hidden;
}

#contact .links {
	display: flex;
	flex-flow: row wrap;
	justify-content: center;
	gap: 5rem;
	margin: auto;
}
</style>
