<script lang="ts">
	export let guides = false;
	export let position: 'in' | 'on' | 'out' = 'in';
	export let direction: 'in' | 'out' | 'up' | 'down' | 'left' | 'right' = 'out';
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
		}
	};

	const transforms = {
		in: {
			t: { x: '-50%', y: '-0%' },
			b: { x: '-50%', y: '-100%' },
			l: { x: '-0%', y: '-50%' },
			r: { x: '-100%', y: '-50%' },
			tl: { x: '-0%', y: '-0%' },
			tr: { x: '-100%', y: '-0%' },
			bl: { x: '-0%', y: '-100%' },
			br: { x: '-100%', y: '-100%' }
		},
		out: {
			t: { x: '-50%', y: '-100%' },
			b: { x: '-50%', y: '-0%' },
			l: { x: '-100%', y: '-50%' },
			r: { x: '-0%', y: '-50%' },
			tl: { x: '-100%', y: '-100%' },
			tr: { x: '-0%', y: '-100%' },
			bl: { x: '-100%', y: '-0%' },
			br: { x: '-0%', y: '-0%' }
		},
		on: {
			t: { x: '-50%', y: '-50%' },
			b: { x: '-50%', y: '-50%' },
			l: { x: '-50%', y: '-50%' },
			r: { x: '-50%', y: '-50%' },
			tl: { x: '-50%', y: '-50%' },
			tr: { x: '-50%', y: '-50%' },
			bl: { x: '-50%', y: '-50%' },
			br: { x: '-50%', y: '-50%' }
		}
	};

	const getSize = (position: Position) => {
		const slot = $$slots[position];
		console.log(slot);
	};

	$: getSize('b');
</script>

<div class={`${styles.container} ${styles.border}`} style={`padding: ${p}; margin: ${m};`}>
	<div class={styles.content}>
		<slot />
	</div>
	<div class={styles.decorations.container}>
		<div
			class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
			style={`width: ${size}; height: ${size}; top: 0%; left: 50%; transform: translate(${transforms[position]?.t.x}, ${transforms[position]?.t.y}) rotate(${rotation[direction].t}deg);`}
		>
			{#if $$slots.t}
				<slot name="t" />
			{:else if guides}
				<span class="text-xs text-gray-500">^</span>
			{/if}
		</div>
		<div
			class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
			style={`width: ${size}; height: ${size}; top: 100%; left: 50%; transform: translate(${transforms[position]?.b.x}, ${transforms[position]?.b.y}) rotate(${rotation[direction].b}deg);`}
		>
			{#if $$slots.b}
				<slot name="b" />
			{:else if guides}
				<span class="text-xs text-gray-500">^</span>
			{/if}
		</div>
		<div
			class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
			style={`width: ${size}; height: ${size}; top: 50%; left: 0%; transform: translate(${transforms[position]?.l.x}, ${transforms[position]?.l.y}) rotate(${rotation[direction].l}deg);`}
		>
			{#if $$slots.l}
				<slot name="l" />
			{:else if guides}
				<span class="text-xs text-gray-500">^</span>
			{/if}
		</div>
		<div
			class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
			style={`width: ${size}; height: ${size}; top: 50%; left: 100%; transform: translate(${transforms[position]?.r.x}, ${transforms[position]?.r.y}) rotate(${rotation[direction].r}deg);`}
		>
			{#if $$slots.r}
				<slot name="r" />
			{:else if guides}
				<span class="text-xs text-gray-500">^</span>
			{/if}
		</div>
		<div
			class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
			style={`width: ${size}; height: ${size}; top: 0%; left: 0%; transform: translate(${transforms[position]?.tl.x}, ${transforms[position]?.tl.y}) rotate(${rotation[direction].tl}deg);`}
		>
			{#if $$slots.tl}
				<slot name="tl" />
			{:else if guides}
				<span class="text-xs text-gray-500">^</span>
			{/if}
		</div>
		<div
			class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
			style={`width: ${size}; height: ${size}; top: 0%; left: 100%; transform: translate(${transforms[position]?.tr.x}, ${transforms[position]?.tr.y}) rotate(${rotation[direction].tr}deg);`}
		>
			{#if $$slots.tr}
				<slot name="tr" />
			{:else if guides}
				<span class="text-xs text-gray-500">^</span>
			{/if}
		</div>
		<div
			class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
			style={`width: ${size}; height: ${size}; top: 100%; left: 0%; transform: translate(${transforms[position]?.bl.x}, ${transforms[position]?.bl.y}) rotate(${rotation[direction].bl}deg);`}
		>
			{#if $$slots.bl}
				<slot name="bl" />
			{:else if guides}
				<span class="text-xs text-gray-500">^</span>
			{/if}
		</div>
		<div
			class={`${styles.decorations.circle} ${guides ? styles.decorations.guides : ''}`}
			style={`width: ${size}; height: ${size}; top: 100%; left: 100%; transform: translate(${transforms[position]?.br.x}, ${transforms[position]?.br.y}) rotate(${rotation[direction].br}deg);`}
		>
			{#if $$slots.br}
				<slot name="br" />
			{:else if guides}
				<span class="text-xs text-gray-500">^</span>
			{/if}
		</div>
	</div>
</div>
