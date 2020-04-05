<script>

	let benchmarkContainer;
	let something = 'asdvt2';
	let asd1 = null;
	let asd2 = null;

	import { afterUpdate } from 'svelte';

	// NONEMPTY DIVS

	// 1
	function add() {
		asd1 = performance.now()
		for (var i = 0; i < 10000; i += 1) {
			const child = document.createElement('div')
			child.setAttribute('id', i)
			child.setAttribute('className', 'benchmarkDiv')
			child.textContent = ('Div ' + i)
			benchmarkContainer.appendChild(child)
		}
		something = !something;
	}

	// 2
	function editOne() {
		asd1 = performance.now()
		const child = document.getElementById('2')
		child.textContent = 'Div ' + Math.random()
		something = !something
	}

	// 3
	function editAll(elementType) {
		asd1 = performance.now()
		let zxc = document.getElementById('benchmarkContainer')
		for (var i = 0; i < zxc.children.length; i += 1) {
			zxc.children[i].textContent = 'Div ' + Math.random()
		}
		something = !something;
	}

	// 4
	function removeOne(elementType) {
		asd1 = performance.now()
		benchmarkContainer.removeChild(document.getElementById(benchmarkContainer.children.length-1))
		something = !something;
	} 

	// 5
	function removeAll(elementType) {
		asd1 = performance.now()
		benchmarkContainer.innerHTML = ''
		something = !something;
	} 

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