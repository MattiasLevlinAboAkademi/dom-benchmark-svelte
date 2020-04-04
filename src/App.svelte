<script>

	let benchmarkContainer;
	let something = 'asdvt2';
	let asd1 = null;
	let asd2 = null;

	import { beforeUpdate, afterUpdate } from 'svelte';

	// NONEMPTY DIVS

	// 1
	function add() {
		asd1 = performance.now()
		something = !something;
		for (var i = 0; i < 10000; i += 1) {
			const child = document.createElement('div')
			child.setAttribute('id', i)
			child.setAttribute('className', 'benchmarkDiv')
			child.textContent = ('Div ' + i)
			benchmarkContainer.appendChild(child)
		}
	}

	// 2
	function editOne() {
		asd1 = performance.now()
		const child = document.getElementById('2')
		child.textContent = 'ddd'
	}

	// 3
	function editAll(elementType) {
		asd1 = performance.now()
		// ...
	}

	// 4
	function removeOne(elementType) {
		asd1 = performance.now()
		benchmarkContainer.removeChild(document.getElementById('2'))
	} 

	// 5
	function removeAll(elementType) {
		asd1 = performance.now()
		benchmarkContainer.innerHTML = ''
	} 

	beforeUpdate(() => {
		// asd2 = performance.now()
		console.log('333')
	});

	afterUpdate(() => {
		asd2 = performance.now()
		console.log('Took ', (asd2 - asd1), ' milliseconds')
	});


</script>

<main>
	<p>B) div, nonempty</p>
	<button on:click={() => add()}>6 add</button>
	<button on:click={editOne}>7 editOne</button>
	<button on:click={editAll}>8 editAll</button>
	<button on:click={removeOne}>9 removeOne</button>
	<button on:click={removeAll}>10 removeAll</button>
	<div
		bind:this={benchmarkContainer}
		id='benchmarkContainer'
	/>
	{{something}}
</main>



<style>
	div {
		background: red;
		color: red;
	}
	button {
		background: red;
		color: red;
	}
</style>