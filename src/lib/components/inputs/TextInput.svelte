<script lang="ts">
	export let className = '';
	export let name: string;
	export let title: string;
	export let text = '';

	$: componentClass = 'input ' + className;
</script>

<div class={componentClass}>
	<label for={name}>{title}</label>
	<input type="text" {name} id={name} bind:value={text} />
</div>

<style>
	.input {
		display: flex;
		flex-direction: column;
	}

	.input:not(:first-of-type) {
		padding-top: 0.5rem;
	}

	.input:last-of-type {
		padding-bottom: 0.5rem;
	}

	.error-message {
		color: red;
	}
</style>
