<script context="module">
	import Checkbox from './Checkbox.svelte';
	import { expect, userEvent } from '@storybook/test';

	export const meta = {
		title: 'Atoms/Checkbox',
		component: Checkbox,
		argTypes: {
			name: { control: 'text' }
		}
	};
</script>

<script>
	import { Story } from '@storybook/addon-svelte-csf';
</script>

<Story
	name="Default"
	play={async ({ canvasElement }) => {
		const checkboxElement = canvasElement.querySelector('input[type="checkbox"]');

		expect(checkboxElement.checked).toBeFalsy();

		userEvent.click(checkboxElement);

		expect(checkboxElement.checked).toBeTruthy();
	}}
>
	<Checkbox />
</Story>

<Story
	name="Checked"
	play={async ({ canvasElement }) => {
		const checkboxElement = canvasElement.querySelector('input[type="checkbox"]');

		expect(checkboxElement.checked).toBeTruthy();

		userEvent.click(checkboxElement);

		expect(checkboxElement.checked).toBeFalsy();
	}}
>
	<Checkbox checked />
</Story>
