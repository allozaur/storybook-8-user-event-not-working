<script context="module">
	import Accordion from './Accordion.svelte';
	import { expect, userEvent } from '@storybook/test';

	export const meta = {
		title: 'Atoms/Accordion',
		component: Accordion,
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
		const detailsElement = canvasElement.querySelector('details');
		const summaryElement = canvasElement.querySelector('summary');

		expect(detailsElement).not.toHaveAttribute('open');

		await userEvent.click(summaryElement);

		expect(detailsElement).toHaveAttribute('open');
	}}
>
	<Accordion />
</Story>

<Story
	name="Open"
	play={async ({ canvasElement }) => {
		const detailsElement = canvasElement.querySelector('details');
		const summaryElement = canvasElement.querySelector('summary');

		expect(detailsElement).toHaveAttribute('open');

		await userEvent.click(summaryElement);

		expect(detailsElement).not.toHaveAttribute('open');
	}}
>
	<Accordion open />
</Story>
