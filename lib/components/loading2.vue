<template>
	<div class="loader-overlay" v-show="visible"></div>
	<div class="pl" v-show="visible">
		<div class="pl__dot" v-for="i in 12" :key="i"></div>
		<div class="pl__text">Loading…</div>
	</div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import { useLoading } from "./modus";

export default defineComponent({
	name: "Loading2",
	props: {
		color: {
			type: String,
			default: "#212121",
		},
		mask: {
			type: String,
			default: "rgb(255 255 255 / 67%)",
		},
	},

	setup(props) {
		const { visible, showLoading, hideLoading } = useLoading();
		return {
			visible,
			showLoading,
			hideLoading,
			color: props.color,
			mask: props.mask,
		};
	},
});
</script>

<style scoped>
.loader-overlay {
	position: fixed;
	top: 0;
	left: 0;
	width: 100vw;
	height: 100vh;
	background: v-bind(mask);
	z-index: 9999;
}
.pl {
	position: fixed;
	z-index: 9999;
	top: 50%;
	left: 50%;
	-webkit-box-shadow: 2em 0 2em rgba(0, 0, 0, 0.2) inset,
		-2em 0 2em rgba(255, 255, 255, 0.1) inset;
	box-shadow: 2em 0 2em rgba(0, 0, 0, 0.2) inset,
		-2em 0 2em rgba(255, 255, 255, 0.1) inset;
	display: -webkit-box;
	display: -ms-flexbox;
	display: flex;
	-webkit-box-pack: center;
	-ms-flex-pack: center;
	justify-content: center;
	-webkit-box-align: center;
	-ms-flex-align: center;
	align-items: center;
	letter-spacing: 0.1em;
	text-transform: uppercase;
	-webkit-transform: translate(-40%, -55%) rotateX(30deg) rotateZ(45deg);
	transform: translate(-40%, -55%) rotateX(30deg) rotateZ(45deg);
	width: 14em;
	height: 14em;
	color: white;
	font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
	background: v-bind(color);
}

.pl,
.pl__dot {
	border-radius: 50%;
}

.pl__dot {
	-webkit-animation-name: shadow724;
	animation-name: shadow724;
	-webkit-box-shadow: 0.1em 0.1em 0 0.1em black,
		0.3em 0 0.3em rgba(0, 0, 0, 0.5);
	box-shadow: 0.1em 0.1em 0 0.1em black, 0.3em 0 0.3em rgba(0, 0, 0, 0.5);
	top: calc(50% - 0.75em);
	left: calc(50% - 0.75em);
	width: 1.5em;
	height: 1.5em;
}

.pl__dot,
.pl__dot:before,
.pl__dot:after {
	-webkit-animation-duration: 2s;
	animation-duration: 2s;
	-webkit-animation-iteration-count: infinite;
	animation-iteration-count: infinite;
	position: absolute;
}

.pl__dot:before,
.pl__dot:after {
	content: "";
	display: block;
	left: 0;
	width: inherit;
	-webkit-transition: background-color var(--trans-dur);
	transition: background-color var(--trans-dur);
}

.pl__dot:before {
	-webkit-animation-name: pushInOut1724;
	animation-name: pushInOut1724;
	background-color: var(--bg);
	border-radius: inherit;
	-webkit-box-shadow: 0.05em 0 0.1em rgba(255, 255, 255, 0.2) inset;
	box-shadow: 0.05em 0 0.1em rgba(255, 255, 255, 0.2) inset;
	height: inherit;
	z-index: 1;
}

.pl__dot:after {
	-webkit-animation-name: pushInOut2724;
	animation-name: pushInOut2724;
	background-color: var(--primary1);
	border-radius: 0.75em;
	-webkit-box-shadow: 0.1em 0.3em 0.2em rgba(255, 255, 255, 0.4) inset,
		0 -0.4em 0.2em #2e3138 inset, 0 -1em 0.25em rgba(0, 0, 0, 0.3) inset;
	box-shadow: 0.1em 0.3em 0.2em rgba(255, 255, 255, 0.4) inset,
		0 -0.4em 0.2em #2e3138 inset, 0 -1em 0.25em rgba(0, 0, 0, 0.3) inset;
	bottom: 0;
	-webkit-clip-path: polygon(0 75%, 100% 75%, 100% 100%, 0 100%);
	clip-path: polygon(0 75%, 100% 75%, 100% 100%, 0 100%);
	height: 3em;
	-webkit-transform: rotate(-45deg);
	-ms-transform: rotate(-45deg);
	transform: rotate(-45deg);
	-webkit-transform-origin: 50% 2.25em;
	-ms-transform-origin: 50% 2.25em;
	transform-origin: 50% 2.25em;
}

.pl__dot:nth-child(1) {
	-webkit-transform: rotate(0deg) translateX(5em) rotate(0deg);
	-ms-transform: rotate(0deg) translateX(5em) rotate(0deg);
	transform: rotate(0deg) translateX(5em) rotate(0deg);
	z-index: 5;
}

.pl__dot:nth-child(1),
.pl__dot:nth-child(1):before,
.pl__dot:nth-child(1):after {
	-webkit-animation-delay: 0s;
	animation-delay: 0s;
}

.pl__dot:nth-child(2) {
	-webkit-transform: rotate(-30deg) translateX(5em) rotate(30deg);
	-ms-transform: rotate(-30deg) translateX(5em) rotate(30deg);
	transform: rotate(-30deg) translateX(5em) rotate(30deg);
	z-index: 4;
}

.pl__dot:nth-child(2),
.pl__dot:nth-child(2):before,
.pl__dot:nth-child(2):after {
	-webkit-animation-delay: -0.1666666667s;
	animation-delay: -0.1666666667s;
}

.pl__dot:nth-child(3) {
	-webkit-transform: rotate(-60deg) translateX(5em) rotate(60deg);
	-ms-transform: rotate(-60deg) translateX(5em) rotate(60deg);
	transform: rotate(-60deg) translateX(5em) rotate(60deg);
	z-index: 3;
}

.pl__dot:nth-child(3),
.pl__dot:nth-child(3):before,
.pl__dot:nth-child(3):after {
	-webkit-animation-delay: -0.3333333333s;
	animation-delay: -0.3333333333s;
}

.pl__dot:nth-child(4) {
	-webkit-transform: rotate(-90deg) translateX(5em) rotate(90deg);
	-ms-transform: rotate(-90deg) translateX(5em) rotate(90deg);
	transform: rotate(-90deg) translateX(5em) rotate(90deg);
	z-index: 2;
}

.pl__dot:nth-child(4),
.pl__dot:nth-child(4):before,
.pl__dot:nth-child(4):after {
	-webkit-animation-delay: -0.5s;
	animation-delay: -0.5s;
}

.pl__dot:nth-child(5) {
	-webkit-transform: rotate(-120deg) translateX(5em) rotate(120deg);
	-ms-transform: rotate(-120deg) translateX(5em) rotate(120deg);
	transform: rotate(-120deg) translateX(5em) rotate(120deg);
	z-index: 1;
}

.pl__dot:nth-child(5),
.pl__dot:nth-child(5):before,
.pl__dot:nth-child(5):after {
	-webkit-animation-delay: -0.6666666667s;
	animation-delay: -0.6666666667s;
}

.pl__dot:nth-child(6) {
	-webkit-transform: rotate(-150deg) translateX(5em) rotate(150deg);
	-ms-transform: rotate(-150deg) translateX(5em) rotate(150deg);
	transform: rotate(-150deg) translateX(5em) rotate(150deg);
	z-index: 1;
}

.pl__dot:nth-child(6),
.pl__dot:nth-child(6):before,
.pl__dot:nth-child(6):after {
	-webkit-animation-delay: -0.8333333333s;
	animation-delay: -0.8333333333s;
}

.pl__dot:nth-child(7) {
	-webkit-transform: rotate(-180deg) translateX(5em) rotate(180deg);
	-ms-transform: rotate(-180deg) translateX(5em) rotate(180deg);
	transform: rotate(-180deg) translateX(5em) rotate(180deg);
	z-index: 2;
}

.pl__dot:nth-child(7),
.pl__dot:nth-child(7):before,
.pl__dot:nth-child(7):after {
	-webkit-animation-delay: -1s;
	animation-delay: -1s;
}

.pl__dot:nth-child(8) {
	-webkit-transform: rotate(-210deg) translateX(5em) rotate(210deg);
	-ms-transform: rotate(-210deg) translateX(5em) rotate(210deg);
	transform: rotate(-210deg) translateX(5em) rotate(210deg);
	z-index: 3;
}

.pl__dot:nth-child(8),
.pl__dot:nth-child(8):before,
.pl__dot:nth-child(8):after {
	-webkit-animation-delay: -1.1666666667s;
	animation-delay: -1.1666666667s;
}

.pl__dot:nth-child(9) {
	-webkit-transform: rotate(-240deg) translateX(5em) rotate(240deg);
	-ms-transform: rotate(-240deg) translateX(5em) rotate(240deg);
	transform: rotate(-240deg) translateX(5em) rotate(240deg);
	z-index: 4;
}

.pl__dot:nth-child(9),
.pl__dot:nth-child(9):before,
.pl__dot:nth-child(9):after {
	-webkit-animation-delay: -1.3333333333s;
	animation-delay: -1.3333333333s;
}

.pl__dot:nth-child(10) {
	-webkit-transform: rotate(-270deg) translateX(5em) rotate(270deg);
	-ms-transform: rotate(-270deg) translateX(5em) rotate(270deg);
	transform: rotate(-270deg) translateX(5em) rotate(270deg);
	z-index: 5;
}

.pl__dot:nth-child(10),
.pl__dot:nth-child(10):before,
.pl__dot:nth-child(10):after {
	-webkit-animation-delay: -1.5s;
	animation-delay: -1.5s;
}

.pl__dot:nth-child(11) {
	-webkit-transform: rotate(-300deg) translateX(5em) rotate(300deg);
	-ms-transform: rotate(-300deg) translateX(5em) rotate(300deg);
	transform: rotate(-300deg) translateX(5em) rotate(300deg);
	z-index: 6;
}

.pl__dot:nth-child(11),
.pl__dot:nth-child(11):before,
.pl__dot:nth-child(11):after {
	-webkit-animation-delay: -1.6666666667s;
	animation-delay: -1.6666666667s;
}

.pl__dot:nth-child(12) {
	-webkit-transform: rotate(-330deg) translateX(5em) rotate(330deg);
	-ms-transform: rotate(-330deg) translateX(5em) rotate(330deg);
	transform: rotate(-330deg) translateX(5em) rotate(330deg);
	z-index: 6;
}

.pl__dot:nth-child(12),
.pl__dot:nth-child(12):before,
.pl__dot:nth-child(12):after {
	-webkit-animation-delay: -1.8333333333s;
	animation-delay: -1.8333333333s;
}

.pl__text {
	font-size: 0.75em;
	max-width: 5rem;
	position: relative;
	text-shadow: 0 0 0.1em var(--fg-t);
	-webkit-transform: rotateZ(-45deg);
	-ms-transform: rotate(-45deg);
	transform: rotateZ(-45deg);
}

/* Animations */
@-webkit-keyframes shadow724 {
	from {
		-webkit-animation-timing-function: ease-in;
		animation-timing-function: ease-in;
		-webkit-box-shadow: 0.1em 0.1em 0 0.1em black,
			0.3em 0 0.3em rgba(0, 0, 0, 0.3);
		box-shadow: 0.1em 0.1em 0 0.1em black, 0.3em 0 0.3em rgba(0, 0, 0, 0.3);
	}

	25% {
		-webkit-animation-timing-function: ease-out;
		animation-timing-function: ease-out;
		-webkit-box-shadow: 0.1em 0.1em 0 0.1em black,
			0.8em 0 0.8em rgba(0, 0, 0, 0.5);
		box-shadow: 0.1em 0.1em 0 0.1em black, 0.8em 0 0.8em rgba(0, 0, 0, 0.5);
	}

	50%,
	to {
		-webkit-box-shadow: 0.1em 0.1em 0 0.1em black,
			0.3em 0 0.3em rgba(0, 0, 0, 0.3);
		box-shadow: 0.1em 0.1em 0 0.1em black, 0.3em 0 0.3em rgba(0, 0, 0, 0.3);
	}
}

@keyframes shadow724 {
	from {
		-webkit-animation-timing-function: ease-in;
		animation-timing-function: ease-in;
		-webkit-box-shadow: 0.1em 0.1em 0 0.1em black,
			0.3em 0 0.3em rgba(0, 0, 0, 0.3);
		box-shadow: 0.1em 0.1em 0 0.1em black, 0.3em 0 0.3em rgba(0, 0, 0, 0.3);
	}

	25% {
		-webkit-animation-timing-function: ease-out;
		animation-timing-function: ease-out;
		-webkit-box-shadow: 0.1em 0.1em 0 0.1em black,
			0.8em 0 0.8em rgba(0, 0, 0, 0.5);
		box-shadow: 0.1em 0.1em 0 0.1em black, 0.8em 0 0.8em rgba(0, 0, 0, 0.5);
	}

	50%,
	to {
		-webkit-box-shadow: 0.1em 0.1em 0 0.1em black,
			0.3em 0 0.3em rgba(0, 0, 0, 0.3);
		box-shadow: 0.1em 0.1em 0 0.1em black, 0.3em 0 0.3em rgba(0, 0, 0, 0.3);
	}
}

@-webkit-keyframes pushInOut1724 {
	from {
		-webkit-animation-timing-function: ease-in;
		animation-timing-function: ease-in;
		background-color: var(--bg);
		-webkit-transform: translate(0, 0);
		transform: translate(0, 0);
	}

	25% {
		-webkit-animation-timing-function: ease-out;
		animation-timing-function: ease-out;
		background-color: var(--primary2);
		-webkit-transform: translate(-71%, -71%);
		transform: translate(-71%, -71%);
	}

	50%,
	to {
		background-color: var(--bg);
		-webkit-transform: translate(0, 0);
		transform: translate(0, 0);
	}
}

@keyframes pushInOut1724 {
	from {
		-webkit-animation-timing-function: ease-in;
		animation-timing-function: ease-in;
		background-color: var(--bg);
		-webkit-transform: translate(0, 0);
		transform: translate(0, 0);
	}

	25% {
		-webkit-animation-timing-function: ease-out;
		animation-timing-function: ease-out;
		background-color: var(--primary2);
		-webkit-transform: translate(-71%, -71%);
		transform: translate(-71%, -71%);
	}

	50%,
	to {
		background-color: var(--bg);
		-webkit-transform: translate(0, 0);
		transform: translate(0, 0);
	}
}

@-webkit-keyframes pushInOut2724 {
	from {
		-webkit-animation-timing-function: ease-in;
		animation-timing-function: ease-in;
		background-color: var(--bg);
		-webkit-clip-path: polygon(0 75%, 100% 75%, 100% 100%, 0 100%);
		clip-path: polygon(0 75%, 100% 75%, 100% 100%, 0 100%);
	}

	25% {
		-webkit-animation-timing-function: ease-out;
		animation-timing-function: ease-out;
		background-color: var(--primary1);
		-webkit-clip-path: polygon(0 25%, 100% 25%, 100% 100%, 0 100%);
		clip-path: polygon(0 25%, 100% 25%, 100% 100%, 0 100%);
	}

	50%,
	to {
		background-color: var(--bg);
		-webkit-clip-path: polygon(0 75%, 100% 75%, 100% 100%, 0 100%);
		clip-path: polygon(0 75%, 100% 75%, 100% 100%, 0 100%);
	}
}

@keyframes pushInOut2724 {
	from {
		-webkit-animation-timing-function: ease-in;
		animation-timing-function: ease-in;
		background-color: var(--bg);
		-webkit-clip-path: polygon(0 75%, 100% 75%, 100% 100%, 0 100%);
		clip-path: polygon(0 75%, 100% 75%, 100% 100%, 0 100%);
	}

	25% {
		-webkit-animation-timing-function: ease-out;
		animation-timing-function: ease-out;
		background-color: var(--primary1);
		-webkit-clip-path: polygon(0 25%, 100% 25%, 100% 100%, 0 100%);
		clip-path: polygon(0 25%, 100% 25%, 100% 100%, 0 100%);
	}

	50%,
	to {
		background-color: var(--bg);
		-webkit-clip-path: polygon(0 75%, 100% 75%, 100% 100%, 0 100%);
		clip-path: polygon(0 75%, 100% 75%, 100% 100%, 0 100%);
	}
}
</style>
