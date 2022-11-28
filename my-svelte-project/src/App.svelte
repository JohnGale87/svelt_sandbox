<script lang="ts">
	export let name: string;
	import Button, { Label } from '@smui/button';
	let clicked = 0;
	let darkThemeInitialState = window.matchMedia("(prefers-color-scheme: dark)").matches;
</script>

<main>
	<h1>Hello {name}!</h1>
	<p>Visit the <a href="https://svelte.dev/tutorial">Svelte tutorial</a> to learn how to build Svelte apps.</p>

	<div>
		<Button on:click={() => {
				clicked++;
				if (clicked % 2 == 0){
					window.document.querySelector('link[href="/build/smui.css"]').disabled = darkThemeInitialState;
					window.document.querySelector('link[href="/build/smui-dark.css"]').disabled = !darkThemeInitialState;
				} else {
					window.document.querySelector('link[href="/build/smui.css"]').disabled = !darkThemeInitialState;
					window.document.querySelector('link[href="/build/smui-dark.css"]').disabled = darkThemeInitialState;
				}
			}}>
		  <Label>Default</Label>
		</Button>
	</div>
	   
	<pre class="status">Clicked: {clicked}</pre>
	
</main>

<style lang="scss">
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;

		@media (min-width: 640px) {
			max-width: none;
		}

		h1 {
			color: #ff3e00;
			text-transform: uppercase;
			font-size: 4em;
			font-weight: 100;
		}
	}
</style>