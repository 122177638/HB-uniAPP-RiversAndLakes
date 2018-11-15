<template>
	<view class="circle-loader-container">
		<view class="loader">
			<view class="text">Loading...</view>
			<view class="horizontal">
			  <view class="circlesup">
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
			  </view>
			  <view class="circlesdwn">
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
			  </view>
			</view>
			<view class="vertical">
			  <view class="circlesup">
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
			  </view>
			  <view class="circlesdwn">
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
					<view class="circle"></view>
			  </view>
			</view>
		</view>
		<!-- <view class="circle-loader" v-if="loadtype == 1">
			<view class="circle-line">
				<view class="circle circle-blue"></view>
				<view class="circle circle-blue"></view>
				<view class="circle circle-blue"></view>
			</view>
			<view class="circle-line">
				<view class="circle circle-yellow"></view>
				<view class="circle circle-yellow"></view>
				<view class="circle circle-yellow"></view>
			</view>
			<view class="circle-line">
				<view class="circle circle-red"></view>
				<view class="circle circle-red"></view>
				<view class="circle circle-red"></view>
			</view>
			<view class="circle-line">
				<view class="circle circle-green"></view>
				<view class="circle circle-green"></view>
				<view class="circle circle-green"></view>
			</view>
		</view> -->
	</view>
</template>

<script>
	export default {
		
	}
</script>

<style scoped>
	view{display: block;}
	.circle-loader-container{position: relative;flex: 1;background-color:rgba(0,0,,0,0.5);}
	/* @-webkit-keyframes rotate-animation {
		0% {
			-webkit-transform: rotate(0deg);
			transform: rotate(0deg);
		}
		100% {
			-webkit-transform: rotate(360deg);
			transform: rotate(360deg);
		}
	}
	@keyframes rotate-animation {
		0% {
			-webkit-transform: rotate(0deg);
			transform: rotate(0deg);
		}
		100% {
			-webkit-transform: rotate(360deg);
			transform: rotate(360deg);
		}
	}
	@-webkit-keyframes move-animation {
		0% {
			-webkit-transform: translate(0, 0);
			transform: translate(0, 0);
		}
		25% {
			-webkit-transform: translate(-64px, 0);
			transform: translate(-64px, 0);
		}
		75% {
			-webkit-transform: translate(32px, 0);
			transform: translate(32px, 0);
		}
		100% {
			-webkit-transform: translate(0, 0);
			transform: translate(0, 0);
		}
	}
	@-webkit-keyframes move-animation {
	 0%{
		 -webkit-transform: translate(0,0);
		 transform: translate(0,0);
	 }
	 }
	@keyframes move-animation {
		0% {
			-webkit-transform: translate(0, 0);
			transform: translate(0, 0);
		}
		25% {
			-webkit-transform: translate(-64px, 0);
			transform: translate(-64px, 0);
		}
		75% {
			-webkit-transform: translate(32px, 0);
			transform: translate(32px, 0);
		}
		100% {
			-webkit-transform: translate(0, 0);
			transform: translate(0, 0);
		}
	}
	body {
		background-color: #F5F5F5;
	}

	.circle-loader {
		display: block;
		width: 64px;
		height: 64px;
		margin-left: -32px;
		margin-top: -32px;
		position: absolute;
		left: 50%;
		top: 50%;
		-webkit-transform-origin: 16px 16px;
		transform-origin: 16px 16px;
		-webkit-animation: rotate-animation 5s infinite;
		animation: rotate-animation 5s infinite;
		-webkit-animation-timing-function: linear;
		animation-timing-function: linear;
	}
	.circle-loader .circle {
		-webkit-animation: move-animation 2.5s infinite;
		animation: move-animation 2.5s infinite;
		-webkit-animation-timing-function: linear;
		animation-timing-function: linear;
		position: absolute;
		left: 50%;
		top: 50%;
	}
	.circle-loader .circle-line {
		width: 64px;
		height: 24px;
		position: absolute;
		top: 4px;
		left: 0;
		-webkit-transform-origin: 4px 4px;
		transform-origin: 4px 4px;
	}
	.circle-loader .circle-line:nth-child(0) {
		-webkit-transform: rotate(0deg);
		transform: rotate(0deg);
	}
	.circle-loader .circle-line:nth-child(1) {
		-webkit-transform: rotate(90deg);
		transform: rotate(90deg);
	}
	.circle-loader .circle-line:nth-child(2) {
		-webkit-transform: rotate(180deg);
		transform: rotate(180deg);
	}
	.circle-loader .circle-line:nth-child(3) {
		-webkit-transform: rotate(270deg);
		transform: rotate(270deg);
	}
	.circle-loader .circle-line .circle:nth-child(1) {
		width: 8px;
		height: 8px;
		top: 50%;
		left: 50%;
		margin-top: -4px;
		margin-left: -4px;
		border-radius: 4px;
		-webkit-animation-delay: -0.3s;
		animation-delay: -0.3s;
	}
	.circle-loader .circle-line .circle:nth-child(2) {
		width: 16px;
		height: 16px;
		top: 50%;
		left: 50%;
		margin-top: -8px;
		margin-left: -8px;
		border-radius: 8px;
		-webkit-animation-delay: -0.6s;
		animation-delay: -0.6s;
	}
	.circle-loader .circle-line .circle:nth-child(3) {
		width: 24px;
		height: 24px;
		top: 50%;
		left: 50%;
		margin-top: -12px;
		margin-left: -12px;
		border-radius: 12px;
		-webkit-animation-delay: -0.9s;
		animation-delay: -0.9s;
	}
	.circle-loader .circle-blue {
		background-color: #1f4e5a;
	}
	.circle-loader .circle-red {
		background-color: #ff5955;
	}
	.circle-loader .circle-yellow {
		background-color: #ffb265;
	}
	.circle-loader .circle-green {
		background-color: #00a691;
	} */
	/* Start the loader code, first, let's align it the center of screen */
	.loader {
		position: absolute;
		top: 50%;
		left: 50%;
		-webkit-transform: translate(-50%, -50%);
		-moz-transform: translate(-50%, -50%);
		-mos-transform: translate(-50%, -50%);
		-o-transform: translate(-50%, -50%);
		transform: translate(-50%, -50%);
		text-align:center;
		-webkit-touch-callout: none;
		-webkit-user-select: none;
		-khtml-user-select: none;
		-moz-user-select: none;
		-ms-user-select: none;
		user-select: none;
		cursor:default;
	}

	/* 	Text align it the center of screen and connect the looped animation for 2 seconds */
	.text{
		position: absolute;
		left: -1.3em;
		top: -1.7em;
		-webkit-animation: text 2s infinite;
		-moz-animation: text 2s infinite;
		-moz-animation: text 2s infinite;
		-ms-animation: text 2s infinite;
		-o-animation: text 2s infinite;
		animation: text 2s infinite;
	}

	/* Set for the first layer vertical position */
	.vertical{
		position:absolute;
		top: -1.84em;
		left: -0.4em;
		-webkit-transform: rotate(90deg);
		-moz-transform: rotate(90deg);
		-ms-transform: rotate(90deg);
		-o-transform: rotate(90deg);
		transform: rotate(90deg);
	}
	/* Set for the second layer horizontal position */
	.horizontal{
		position:absolute;
		top:0em;
		left:0em;
		-webkit-transform: rotate(0deg);
		-moz-transform: rotate(0deg);
		-ms-transform: rotate(0deg);
		-o-transform: rotate(0deg);
		transform: rotate(0deg);
	}
	/* The next two classes do mirror for animation */
	.circlesup{
		position:absolute;
		top: -4.7em;
		right: 12.1em;
	}
	.circlesdwn{
		position:absolute;
		top:2.5em;
		right:-13.5em;
		-webkit-transform: rotate(180deg);
		-moz-transform: rotate(180deg);
		-ms-transform: rotate(180deg);
		-o-transform: rotate(180deg);
		transform: rotate(180deg);
	}

	/* Create a container for our circles, rotate it 45 degrees and set animation*/
	.circle {
		position: absolute;
		width:15em;
		height: 15em;
		-webkit-transform: rotate(45deg);
		-moz-transform: rotate(45deg);
		-ms-transform: rotate(45deg);
		-o-transform: rotate(45deg);
		transform: rotate(45deg);
		-webkit-animation: orbit 2s infinite;
		-moz-animation: orbit 2s infinite;
		-moz-animation: orbit 2s infinite;
		-ms-animation: orbit 2s infinite;
		-o-animation: orbit 2s infinite;
		animation: orbit 2s infinite;
		z-index:5;
	} 
	/* Style's of our circles */
	.circle:after {
		content: '';
		position: absolute;
		width: 2em;
		height: 2em;
		-webkit-border-radius: 100%;
		-moz-border-radius: 100%;
		-ms-border-radius: 100%;
		-o-border-radius: 100%;
		border-radius: 100%;
		background: #13A3A5; /* Pick a color 1*/
	}
	.circle:nth-child(2) {
		-webkit-animation-delay: 100ms; 
		-moz-animation-delay: 100ms; 
		-ms-animation-delay: 100ms; 
		-o-animation-delay: 100ms; 
		animation-delay: 100ms;
		z-index:4;
	}
	.circle:nth-child(2):after  {
		background: #56bebf; /* Pick a color 2*/
		-webkit-transform: scale(0.8,0.8);
		-moz-transform: scale(0.8,0.8);
		-ms-transform: scale(0.8,0.8);
		-o-transform: scale(0.8,0.8);
		transform: scale(0.8,0.8);
	}
	.circle:nth-child(3) {
		-webkit-animation-delay: 225ms; 
		-moz-animation-delay: 225ms; 
		-ms-animation-delay: 225ms; 
		-o-animation-delay: 225ms; 
		animation-delay: 225ms; 
		z-index:3;
	}
	.circle:nth-child(3):after  {
		background: #ffa489; /* Pick a color 3*/
		-webkit-transform: scale(0.6,0.6);
		-moz-transform: scale(0.6,0.6);
		-ms-transform: scale(0.6,0.6);
		-o-transform: scale(0.6,0.6);
		transform: scale(0.6,0.6);
	}
	.circle:nth-child(4) {
		-webkit-animation-delay: 350ms; 
		-moz-animation-delay: 350ms; 
		-ms-animation-delay: 350ms; 
		-o-animation-delay: 350ms; 
		animation-delay: 350ms; 
		z-index:2;
	}
	.circle:nth-child(4):after  {
		background: #ff6d37; /* Pick a color 4*/
		-webkit-transform: scale(0.4,0.4);
		-moz-transform: scale(0.4,0.4);
		-ms-transform: scale(0.4,0.4);
		-o-transform: scale(0.4,0.4);
		transform: scale(0.4,0.4);
	}
	.circle:nth-child(5) {
		-webkit-animation-delay: 475ms; 
		-moz-animation-delay: 475ms; 
		-ms-animation-delay: 475ms; 
		-o-animation-delay: 475ms; 
		animation-delay: 475ms; 
		z-index:1;
	}
	.circle:nth-child(5):after  {
		background: #DB2F00; /* Pick a color 5*/
		-webkit-transform: scale(0.2,0.2);
		-moz-transform: scale(0.2,0.2);
		-ms-transform: scale(0.2,0.2);
		-o-transform: scale(0.2,0.2);
		transform: scale(0.2,0.2);
	}
	/* Animation keys */
	@keyframes orbit { 
		0%{ transform:rotate(45deg); } 
		5%{ transform:rotate(45deg);animation-timing-function: ease-out; } 
		70%{ transform:rotate(405deg);animation-timing-function: ease-in; }
		100%{ transform:rotate(405deg); } 
	}
	@keyframes text {
		0%{ transform:scale(0.2,0.2);animation-timing-function: ease-out; } 
		50%{ transform:scale(1,1); animation-timing-function: ease-out;  }
		60%{ transform:scale(1,1); animation-timing-function: ease-out;  }
		100%{ transform:scale(0.2,0.2);  } 
	}
</style>
