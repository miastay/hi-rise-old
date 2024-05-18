<script>
	import MaterialApp from "svelte-materialify/src/components/MaterialApp/MaterialApp.svelte";
	import Button from "svelte-materialify/src/components/Button/Button.svelte";
    import { AppBar } from "svelte-materialify";
    import Inputs from "$lib/Inputs.svelte";
    import Plot from "$lib/Plot.svelte";
    import Options from "$lib/Options.svelte";
    import About from "$lib/About.svelte";
</script>

<MaterialApp>
	<AppBar class="primary-color">
		<span slot="title" class="white-text">hi-rise v1a</span>
	</AppBar>
	<div class="appgrid">
		<div class="flex">
			<About />
			<Inputs />
		</div>
		<div class="spaced">
			<Plot />
			<Options />
		</div>
	</div>
</MaterialApp>

<style lang="scss">
	$pad: 1rem;
	.appgrid {
		padding: $pad;
		display: grid;
		grid-template-columns: 2fr 5fr;
		gap: $pad;
		.spaced {
			display: grid;
			grid-template-rows: 3fr 2fr;
			gap: $pad;
		}
		.flex {
			display: flex;
			flex-direction: column;
			gap: $pad;
		}
	}
</style>