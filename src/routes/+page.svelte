<script lang="ts">
	import Frame from '$lib/components/frame/Frame.svelte';
	import Surface from '$lib/components/surface/Surface.svelte';
	import Flower_1 from '$lib/assets/2d/decoration_flower_1.png';
	import Flower_2 from '$lib/assets/2d/decoration_flower_2.png';
	import Flower_3 from '$lib/assets/2d/decoration_flower_3.png';
	import Flower_4 from '$lib/assets/2d/decoration_flower_4.png';
	import Flower_5 from '$lib/assets/2d/decoration_flower_5.png';
	import Flower_6 from '$lib/assets/2d/decoration_flower_6.png';
	import Flower_7 from '$lib/assets/2d/decoration_flower_7.png';
	import Flower_8 from '$lib/assets/2d/decoration_flower_8.png';
	import Border_1 from '$lib/assets/2d/decoration_border_1.png';
	import Border_2 from '$lib/assets/2d/decoration_border_2.png';
	import Border_3 from '$lib/assets/2d/decoration_border_3.png';
	import Border_4 from '$lib/assets/2d/decoration_border_4.png';
	import BG_1 from '$lib/assets/2d/gothic_background_1.webp';
	import BG_2 from '$lib/assets/2d/gothic_background_2.webp';
	import Corner_1 from '$lib/assets/2d/decoration_corner_1.png';
</script>

<Frame bg={BG_1} size="500px" direction="up" position="on" guides={false} p={'40px'} m={'50px'}>
	<div slot="t"><img src={Border_1} alt="" /></div>
	<div slot="b"><img src={Border_4} alt="" /></div>
	<div>
		<h1>Welcome to your library project</h1>
		<p>Create your package using @sveltejs/package and preview/showcase your work with SvelteKit</p>
		<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
	</div>
</Frame>
<Frame size="300px" direction="in" position="on" guides={false} p={'70px'} m={'80px'}>
	<div slot="l"><img src={Border_2} alt="" /></div>
	<div slot="r"><img src={Border_3} alt="" /></div>
	<Surface>
		<h1>Welcome to your library project</h1>
		<p>Create your package using @sveltejs/package and preview/showcase your work with SvelteKit</p>
		<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
	</Surface>
</Frame>

<Frame size="50px" direction="out" position="out" guides={false} p={'30px'} m={'80px'}>
	<div slot="t"><img src={Flower_1} alt="" /></div>
	<div slot="b"><img src={Flower_2} alt="" /></div>
	<div slot="l"><img src={Flower_3} alt="" /></div>
	<div slot="r"><img src={Flower_4} alt="" /></div>
	<div slot="tl"><img src={Flower_5} alt="" /></div>
	<div slot="tr"><img src={Flower_6} alt="" /></div>
	<div slot="bl"><img src={Flower_7} alt="" /></div>
	<div slot="br"><img src={Flower_8} alt="" /></div>

	<Surface>
		<h1>Welcome to your library project</h1>
		<p>Create your package using @sveltejs/package and preview/showcase your work with SvelteKit</p>
		<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
	</Surface>
</Frame>

<Frame size="80px" direction="revolve" position="in" guides={false} p={'50px'} m={'80px'}>
	<div slot="tl"><img src={Corner_1} alt="" /></div>
	<div slot="br"><img src={Corner_1} alt="" /></div>

	<Surface>
		<h1>Welcome to your library project</h1>
		<p>Create your package using @sveltejs/package and preview/showcase your work with SvelteKit</p>
		<p>Visit <a href="https://kit.svelte.dev">kit.svelte.dev</a> to read the documentation</p>
	</Surface>
</Frame>
