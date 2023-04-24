<script lang="ts">
	import { enhance } from '$app/forms';
</script>

<svelte:head>
	<title>Home</title>
	<meta name="description" content="Svelte demo app" />
</svelte:head>

<section>
	<form
		method="POST"
		action="?/test"
		use:enhance={() => {
			return ({ result, update }) => {
				if (result.type === 'success') {
					const x = result.data?.hello;
					console.log({ x });
				}
				update();
			};
		}}
	>
		<input type="text" name="temp" id="temp" />
	</form>
</section>

<style>
	section {
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		flex: 0.6;
	}
</style>
