<script lang="ts">
	import Surface from '../surface/Surface.svelte';

	export let guides = false;
	export let bg = '';
	export let position: 'in' | 'on' | 'out' = 'in';
	export let direction: 'in' | 'out' | 'up' | 'down' | 'left' | 'right' | 'revolve' = 'out';
	export let p = '10px';
	export let m = '10px';
	export let size = '40px';

	type Position = 't' | 'b' | 'l' | 'r' | 'tl' | 'tr' | 'bl' | 'br';

	const styles = {
		container: `relative inline-block `,
		border: 'border-2 border-gray-200 ',
		content: 'relative',
		decorations: {
			container: '',
			guides: 'border border-1 border-red-500 rounded-full',
			circle: 'absolute transform flex justify-center items-center'
		}
	};

	const rotation = {
		in: {
			t: '180',
			b: '0',
			l: '90',
			r: '270',
			tl: '125',
			tr: '-125',
			bl: '45',
			br: '-45'
		},
		out: {
			t: '0',
			b: '180',
			l: '270',
			r: '90',
			tl: '-45',
			tr: '45',
			bl: '225',
			br: '125'
		},
		up: {
			t: '0',
			b: '0',
			l: '0',
			r: '0',
			tl: '0',
			tr: '0',
			bl: '0',
			br: '0'
		},
		down: {
			t: '180',
			b: '180',
			l: '180',
			r: '180',
			tl: '180',
			tr: '180',
			bl: '180',
			br: '180'
		},
		left: {
			t: '-90',
			b: '-90',
			l: '-90',
			r: '-90',
			tl: '-90',
			tr: '-90',
			bl: '-90',
			br: '-90'
		},
		right: {
			t: '90',
			b: '90',
			l: '90',
			r: '90',
			tl: '90',
			tr: '90',
			bl: '90',
			br: '90'
		},
		revolve: {
			t: '90',
			b: '90',
			l: '90',
			r: '90',
			tl: '180',
			tr: '270',
			bl: '90',
			br: '0'
		}
	};

	const transforms = {
		in: {
			t: { x: '5', y: '' },
			b: { x: '5', y: '10' },
			l: { x: '', y: '5' },
			r: { x: '10', y: '5' },
			tl: { x: '', y: '' },
			tr: { x: '10', y: '' },
			bl: { x: '', y: '10' },
			br: { x: '10', y: '10' }
		},
		out: {
			t: { x: '5', y: '10' },
			b: { x: '5', y: '' },
			l: { x: '10', y: '5' },
			r: { x: '0', y: '5' },
			tl: { x: '10', y: '10' },
			tr: { x: '', y: '10' },
			bl: { x: '10', y: '' },
			br: { x: '', y: '' }
		},
		on: {
			t: { x: '5', y: '5' },
			b: { x: '5', y: '5' },
			l: { x: '5', y: '5' },
			r: { x: '5', y: '5' },
			tl: { x: '5', y: '5' },
			tr: { x: '5', y: '5' },
			bl: { x: '5', y: '5' },
			br: { x: '5', y: '5' }
		}
	};

	const getSize = (position: Position) => {
		const slot = $$slots[position];
		console.log(slot);
	};

	$: getSize('b');
</script>

<div class={`${styles.container} ${styles.border}`} style={`margin: ${m};`}>
	<div style={`padding: ${p};`}>
		<div class={styles.content}>
			<slot />
		</div>
		<div class={styles.decorations.container}>
			{#if $$slots.t || guides}
				<div
					class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
					style={`width: ${size}; height: ${size}; top: 0%; left: 50%; transform: translate(-${transforms[position]?.t.x}0%, -${transforms[position]?.t.y}0%) rotate(${rotation[direction].t}deg);`}
				>
					{#if $$slots.t}
						<slot name="t" />
					{:else if guides}
						<span class="text-xs text-gray-500">^</span>
					{/if}
				</div>
			{/if}
			{#if $$slots.b || guides}
				<div
					class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
					style={`width: ${size}; height: ${size}; top: 100%; left: 50%; transform: translate(-${transforms[position]?.b.x}0%, -${transforms[position]?.b.y}0%) rotate(${rotation[direction].b}deg);`}
				>
					{#if $$slots.b}
						<slot name="b" />
					{:else if guides}
						<span class="text-xs text-gray-500">^</span>
					{/if}
				</div>
			{/if}
			{#if $$slots.l || guides}
				<div
					class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
					style={`width: ${size}; height: ${size}; top: 50%; left: 0%; transform: translate(-${transforms[position]?.l.x}0%, -${transforms[position]?.l.y}0%) rotate(${rotation[direction].l}deg);`}
				>
					{#if $$slots.l}
						<slot name="l" />
					{:else if guides}
						<span class="text-xs text-gray-500">^</span>
					{/if}
				</div>
			{/if}
			{#if $$slots.r || guides}
				<div
					class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
					style={`width: ${size}; height: ${size}; top: 50%; left: 100%; transform: translate(-${transforms[position]?.r.x}0%, -${transforms[position]?.r.y}0%) rotate(${rotation[direction].r}deg);`}
				>
					{#if $$slots.r}
						<slot name="r" />
					{:else if guides}
						<span class="text-xs text-gray-500">^</span>
					{/if}
				</div>
			{/if}
			{#if $$slots.tl || guides}
				<div
					class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
					style={`width: ${size}; height: ${size}; top: 0%; left: 0%; transform: translate(-${transforms[position]?.tl.x}0%, -${transforms[position]?.tl.y}0%) rotate(${rotation[direction].tl}deg);`}
				>
					{#if $$slots.tl}
						<slot name="tl" />
					{:else if guides}
						<span class="text-xs text-gray-500">^</span>
					{/if}
				</div>
			{/if}
			{#if $$slots.tr || guides}
				<div
					class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
					style={`width: ${size}; height: ${size}; top: 0%; left: 100%; transform: translate(-${transforms[position]?.tr.x}0%, -${transforms[position]?.tr.y}0%) rotate(${rotation[direction].tr}deg);`}
				>
					{#if $$slots.tr}
						<slot name="tr" />
					{:else if guides}
						<span class="text-xs text-gray-500">^</span>
					{/if}
				</div>
			{/if}
			{#if $$slots.bl || guides}
				<div
					class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
					style={`width: ${size}; height: ${size}; top: 100%; left: 0%; transform: translate(-${transforms[position]?.bl.x}0%, -${transforms[position]?.bl.y}0%) rotate(${rotation[direction].bl}deg);`}
				>
					{#if $$slots.bl}
						<slot name="bl" />
					{:else if guides}
						<span class="text-xs text-gray-500">^</span>
					{/if}
				</div>
			{/if}
			{#if $$slots.br || guides}
				<div
					class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
					style={`width: ${size}; height: ${size}; top: 100%; left: 100%; transform: translate(-${transforms[position]?.br.x}0%, -${transforms[position]?.br.y}0%) rotate(${rotation[direction].br}deg);`}
				>
					{#if $$slots.br}
						<slot name="br" />
					{:else if guides}
						<span class="text-xs text-gray-500">^</span>
					{/if}
				</div>
			{/if}
		</div>
	</div>
</div>
