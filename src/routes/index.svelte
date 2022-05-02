<script>
	import * as THREE from 'three';

	let key;
	let keyCode;

	function handleKeydown(event) {
		key = event.key;
		keyCode = event.keyCode;
		const audio = document.querySelector(`audio[data-key="${keyCode}"]`);
		//stop function if there is no audio associated with key
		if (!audio) return;
		//rewind to start, prevents audio from stalling
		audio.volume = 0.2;
		audio.currentTime = 0;
		audio.play();
	}

	function removeTransition(e) {}

	// const keys = document.querySelectorAll('.key');
	// keys.forEach((key) => key.addEventListener('transitionend', removeTransition));
</script>

<svelte:head>
	<title>3D Drum Kit</title>
</svelte:head>

<svelte:window on:keydown={handleKeydown} />

<div class="background--custom">
	<canvas id="canvas" />
</div>

<div class="keys">
	<div data-key="65" class="key">
		<kbd>A</kbd>
		<span class="sound">clap</span>
	</div>
	<div data-key="83" class="key">
		<kbd>S</kbd>
		<span class="sound">hihat</span>
	</div>
	<div data-key="68" class="key">
		<kbd>D</kbd>
		<span class="sound">kick</span>
	</div>
	<div data-key="70" class="key">
		<kbd>F</kbd>
		<span class="sound">openhat</span>
	</div>
	<div data-key="71" class="key">
		<kbd>G</kbd>
		<span class="sound">boom</span>
	</div>
	<div data-key="72" class="key">
		<kbd>H</kbd>
		<span class="sound">ride</span>
	</div>
	<div data-key="74" class="key">
		<kbd>J</kbd>
		<span class="sound">snare</span>
	</div>
	<div data-key="75" class="key">
		<kbd>K</kbd>
		<span class="sound">tom</span>
	</div>
	<div data-key="76" class="key">
		<kbd>L</kbd>
		<span class="sound">tink</span>
	</div>
</div>

<audio data-key="65" src="clap.wav" />
<audio data-key="83" src="hihat.wav" />
<audio data-key="68" src="kick.wav" />
<audio data-key="70" src="openhat.wav" />
<audio data-key="71" src="boom.wav" />
<audio data-key="72" src="ride.wav" />
<audio data-key="74" src="snare.wav" />
<audio data-key="75" src="tom.wav" />
<audio data-key="76" src="tink.wav" />

<style>
	.background--custom {
		background-color: #000000;
		width: 100vw;
		height: 100vh;
		position: absolute;
		overflow: hidden;
		z-index: -2;
		top: 0;
		left: 0;
	}
	canvas#canvas {
		z-index: -1;
		position: absolute;
		width: 100%;
		height: 60%;
		transform: rotate(0deg) scale(2) translateY(0%);
		--gradient-color-1: #e4e4e4;
		--gradient-color-2: #b0c0e2;
		--gradient-color-3: #c69ac9;
		--gradient-color-4: #aeaeb8;
		--gradient-speed: 0.000008;
	}
</style>
