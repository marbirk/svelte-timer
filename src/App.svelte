<script lang="ts">
	import Ring from './Ring.svelte';
	import Timer from './Timer.svelte';
</script>

<main>
	<div class="wrapper">
		<Ring />
		<Timer />
	</div>
</main>

<style>
	.wrapper {
		align-items: center;
		border-radius: 50%;
		box-shadow: -5px 14px 44px #000000, 5px -16px 50px rgba(255, 255, 255, 0.15);
		display: flex;
		height: 518px;
		justify-content: center;
		position: relative;
		width: 518px;
	}
</style>