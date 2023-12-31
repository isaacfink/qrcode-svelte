<script lang="ts">
	import './styles.css';
	import { QrCode } from '$lib';

	const loremText =
		'Lorem ipsum dolor sit amet consectetur adipisicing elit. Natus, blanditiis quod modi voluptates, iste distinctio nisi, earum esse officia cumque harum vel. ad!';
</script>

<div class="bg-slate-800 py-16">
	<div class="max-w-2xl mx-auto bg-slate-800">
		<h1 class="text-5xl mx-auto mb-12 text-slate-100 text-center">qrcode-svelte</h1>
		<p class="text-center prose text-slate-300 text-xl">
			A simple component for generating QR codes in Svelte.
		</p>
		<QrCode
			svgClass="bg-slate-800"
			squareClass="text-white fill-current"
			value={'https://google.com'}
			errorCorrection="H"
			border={5}
		/>
	</div>
</div>
