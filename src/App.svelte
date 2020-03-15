<script>

	let benchmarkContainer;

	// A EMPTY DIVS

	// 1
	function addEmpty(elementType) {
		for (var i = 0; i < 10000; i += 1) {
			const child = document.createElement(elementType)
			child.setAttribute('id', i)
			child.setAttribute('className', 'benchmarkDiv')
			benchmarkContainer.appendChild(child)
		}
	}

	// 2
	function editOneEmpty(elementType) {
		// ...
	}

	// 3
	function editAllEmpty(elementType) {
		// ...
	}

	// 4
	function removeOneEmpty(elementType) {
		// ...
	} 

	// 5
	function removeAllEmpty(elementType) {
		// ...
	} 

	// B NONEMPTY DIVS

	// 6
	function add(elementType) {
		for (var i = 0; i < 10000; i += 1) {
			const child = document.createElement(elementType)
			child.setAttribute('id', i)
			child.setAttribute('className', 'benchmarkDiv')
			child.textContent = (elementType + ' ' + i)
			benchmarkContainer.appendChild(child)
		}
	}

	// 7
	function editOne() {
		const child = document.getElementById('2')
		child.textContent = 'ddd'
	}

	// 8
	function editAll(elementType) {
		// ...
	}

	// 9
	function removeOne(elementType) {
		// ...
	} 

	// 10
	function removeAll(elementType) {
		// ...
	} 
</script>

<main>
	<p>A) div, empty</p>
	<button on:click={() => addEmpty("div")}>1 add</button>
	<button on:click={() => editOneEmpty("div")}>2 editOne</button>
	<button on:click={() => editAllEmpty("div")}>3 editAll</button>
	<button on:click={() => removeOneEmpty("div")}>4 removeOne</button>
	<button on:click={() => removeAllEmpty("div")}>5 removeOne</button>
	<p>B) div, nonempty</p>
	<button on:click={() => add("div")}>6 add</button>
	<button on:click={editOne}>7 editOne</button>
	<button on:click={editAll}>8 editAll</button>
	<button on:click={removeOne}>9 removeOne</button>
	<button on:click={removeAll}>10 removeAll</button>
	<p>C) svg, empty</p>
	<button on:click={() => addEmpty("svg")}>11 add</button>
	<button on:click={editOneEmpty}>12 editOne</button>
	<button on:click={editAllEmpty}>13 editAll</button>
	<button on:click={removeOneEmpty}>14 removeOne</button>
	<button on:click={removeAllEmpty}>15 removeAll</button>
	<p>D) svg, nonempty</p>
	<button on:click={() => add("svg")}>16 add</button>
	<button on:click={editOne}>17 editOne</button>
	<button on:click={editAll}>18 editAll</button>
	<button on:click={removeOne}>19 removeOne</button>
	<button on:click={removeAll}>20 removeAll</button>
	<div
		bind:this={benchmarkContainer}
		id='benchmarkContainer'
	/>
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