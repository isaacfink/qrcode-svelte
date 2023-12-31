<script lang="ts">
	import { Ecc, QrCode } from './internal/qrcode';
	import type { ErrorCorrectionLevel, Mode, Version } from './types';

	export let value: string;
	export let errorCorrection: ErrorCorrectionLevel = 'L';
	export let border: number = 2;
	export let svgClass: string = '';
	export let squareClass: string = '';

	const ecl =
		errorCorrection === 'H'
			? Ecc.HIGH
			: errorCorrection === 'Q'
			? Ecc.QUARTILE
			: errorCorrection === 'M'
			? Ecc.MEDIUM
			: Ecc.LOW;

	const code = QrCode.encodeText(value, ecl);
</script>

<svg
	width="100%"
	height="100%"
	viewBox={`0 0 ${code.size * 10 + border * 2} ${code.size * 10 + border * 2}`}
	class={svgClass}
>
	{#each { length: code.size } as _, y}
		{#each { length: code.size } as _, x}
			{@const element = code.getModule(x, y)}
			{#if element}
				<rect
					x={x * 10 + border}
					y={y * 10 + border}
					width="10.2"
					height="10.2"
					fill="black"
					class={squareClass}
					stroke="none"
				/>
			{/if}
		{/each}
	{/each}
</svg>
