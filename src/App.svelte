<script>
    export let name;
	let text = '';
	let version = 8;
	function assign() {
		name = 'java'
		version = 11
	}
	let toggle = false;
	let Apple = ['iPhone', 'Mac', 'iPad', 'Watch', 'AirPods'];
	function rich() {
		Apple = Apple.slice(1);
	}
</script>

<main>
	<button on:click={() => {toggle = !toggle}}>
		TOGGLE
	</button>
	{#if toggle === true}
		<h1>Hello {name}!</h1>
	{:else}
		<h1>SUN OF A BITCH {name}!</h1>
	{/if}
	<h2 class={version > 8 ? 'active' : ''}>V.{version}</h2>
	<button on:click={assign}>ASSIGN</button>
	<input type="text" placeholder="{name}" style="width: 200px;"/>
	<ul>
		{#each Apple as apple}
			<li>{apple}</li>
		{/each}
	</ul>
	<button on:click={rich}>
		FLEX 🤑
	</button>
	<h2>PRODUCTS REVERSE</h2>
	<!-- ...[ARRAY]는 배열을 COPY 하면서 서로 다른 메모리 주소를 참조하게 만든다. -->
	<ul>
		{#each [...Apple].reverse() as apple}
			<li>{apple}</li>
		{/each}
	</ul>
	<h2>INPUT TEXT >>> {text}</h2>
	<input type="text" value="{text}" on:input = {(e) => {text = e.target.value}} />
	<button on:click = {() => {text = 'System.out.println("hello");'}}>
		Click Me!
	</button>
</main>

<style>
    main {
        text-align: center;
        padding: 1em;
        max-width: 240px;
        margin: 0 auto;
    }

    h1 {
        color: #ff3e00;
        text-transform: uppercase;
        font-size: 4em;
        font-weight: 100;
    }

	.active {
		color: blue;
	}

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>
