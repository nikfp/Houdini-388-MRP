<script lang="ts">
	import TextInput from './components/inputs/TextInput.svelte';
	import NumberInput from './components/inputs/NumberInput.svelte';
	import { GQL_SendIt } from '$houdini';

	let text = '';
	let number = 0;

	async function handleSubmit() {
		await GQL_SendIt.mutate({
			variables: {
				input: {
					words: text,
					numbers: number
				}
			}
		});
	}

	// const { form, errors } = createForm<Input>({
	// 	onSubmit: async (values) => {
	// 		const input = sendInputSchema.parse(values);
	// 		await GQL_SendIt.mutate({ variables: { input } });
	// 	},
	// 	onError: (error) => {
	// 		console.log('ERRORS');
	// 		console.log(error);
	// 	},
	// 	onSuccess: (_success) => {
	// 		console.log('SUCCESS');
	// 		console.log($GQL_SendIt.data?.send.send);
	// 	},
	// 	extend: [validator({ schema: sendInputSchema }), reporter]
	// });
</script>

<p>
	{JSON.stringify($GQL_SendIt.data)}
</p>
<form on:submit={handleSubmit}>
	<TextInput title="Words" {text} name="words" />
	<NumberInput title="Numbers" {number} name="numbers" />
	<button type="submit">Submit</button>
</form>

<style>
	form {
		display: flex;
		flex-direction: column;
		max-width: 30rem;
	}
</style>
