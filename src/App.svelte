<script>
	import { fade, scale } from 'svelte/transition';
	import { flip } from 'svelte/animate';
 let array = [0, 1, 2, 3, 4];

 let returned = '';

 function pop() {
	 returned = array.pop();
	 array=array;
 }

 function push() {
	 if (array.length > 0) {
	 	returned = array.push(array[array.length - 1] + 1);
	 	array = array
	 } else {
		returned = array.push(0);
		array = array;
	 }
 }

 function shift() {
	 returned = array.shift();
	 array = array;
 }

 function unshift() {
	 if (array.length > 0) {
		returned = array.unshift(array[0] - 1);
		array = array;
	 } else {
		returned = array.unshift(0);
		array = array; 
	 }
 }

</script>

<style>
	:global(body) {
		color: #000;
	}

	h1 {
		color: #4E7;
		text-shadow: -.125rem .125rem 0 #B5F;
		font-size: 3.25rem;
		transform: rotate(-9deg);
		margin-bottom: 2em;
	}

	.array {
		display: flex;
		gap: .25em;
		height: 3em;
	}

	.element {
		width: 3em;
		height: 3em;
		background-color: #5F8;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 2px solid black;
	}

	.returned {
		width: 3em;
		height: 3em;
		background-color: #FF5599;
		display: flex;
		align-items: center;
		justify-content: center;
		border: 2px solid black;
		margin-bottom: 2rem;
	}

	button {
		color: #000;
		background-color: #BB99FF;
		padding: .75em 1.5em;
		border: 2px solid black;
		border-radius: .25em;
		box-shadow: -.25em .25em 0 #000;
		cursor: pointer;
	}

	button + button { margin-left: .5em}
</style>
<h1>Fun with Arrays!</h1>
	
<h3>array:</h3>
<div class= "array">
	{#each array as element, i (element)}
		<div animate:flip="{{ duration: 300 }}" out:scale="{{ duration: 250 }}" in:scale="{{ duration: 250 }}" class="element">{element}</div>
	{/each}
</div>
<h3>returned:</h3>

<div class="returned">
	{returned}
</div>

<button on:click={pop}>pop</button>
<button on:click={push}>push</button>
<button on:click={shift}>shift</button>
<button on:click={unshift}>unshift</button>