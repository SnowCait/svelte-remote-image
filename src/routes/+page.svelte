<script lang="ts">
import type { ImgSrc, PictureSrc } from '$lib/components/type.js'
import { Picture, Img } from '$lib/index.js'

const optimazerPrefix = 'https://nostr-image-optimizer.ocknamo.com/image/'
const originalImageUrl =
	'https://ocknamo.com/static/b84d6366deec053ff3fa77df01a54464/dccd3/cat.webp'
const invalidImageUrl =
	'https://ocknamo.com/static/b84d6366deec053ff3fa77df01a54464/dccd3/cat.web'
const fallbackImageUrl =
	'https://ocknamo.com/static/0bbd27c7f38d84c4ae95b9c81e17693c/0fe81/I_love_Bitcoin.webp'

const imgSrc: ImgSrc = {
	w: 800,
	img: `${optimazerPrefix}width=1600,quality=70,format=webp/${originalImageUrl}`,
	srcsets: [
		{
			src: `${optimazerPrefix}width=1600,quality=50,format=webp/${originalImageUrl}`,
			w: 1600,
		},
		{
			src: `${optimazerPrefix}width=800,quality=50,format=webp/${originalImageUrl}`,
			w: 800,
		},
	],
	fallback: [originalImageUrl, fallbackImageUrl],
}

const fallImageSrc: ImgSrc = {
	w: 800,
	img: `${optimazerPrefix}width=1600,quality=70,format=webp/${invalidImageUrl}`,
	srcsets: [
		{
			src: `${optimazerPrefix}width=1600,quality=50,format=webp/${invalidImageUrl}`,
			w: 1600,
		},
		{
			src: `${optimazerPrefix}width=800,quality=50,format=webp/${invalidImageUrl}`,
			w: 800,
		},
	],
	fallback: [invalidImageUrl, fallbackImageUrl],
}

const src: PictureSrc = {
	w: 800,
	img: `${optimazerPrefix}width=1600,quality=70,format=webp/${originalImageUrl}`,
	webp: [
		{
			src: `${optimazerPrefix}width=1600,quality=50,format=webp/${originalImageUrl}`,
			w: 1600,
		},
		{
			src: `${optimazerPrefix}width=800,quality=50,format=webp/${originalImageUrl}`,
			w: 800,
		},
	],
	jpeg: [
		{
			src: `${optimazerPrefix}width=1600,quality=50,format=jpeg/${originalImageUrl}`,
			w: 1600,
		},
		{
			src: `${optimazerPrefix}width=800,quality=50,format=jpeg/${originalImageUrl}`,
			w: 800,
		},
	],
	fallback: [originalImageUrl, fallbackImageUrl],
	placeholder: { dataUri: '', color: '#c5c5c5' },
	blur: true,
}

const blurFalseSrc: PictureSrc = {
	w: 800,
	img: `${optimazerPrefix}width=1600,quality=70,format=webp/${originalImageUrl}`,
	webp: [
		{
			src: `${optimazerPrefix}width=1600,quality=50,format=webp/${originalImageUrl}`,
			w: 1600,
		},
		{
			src: `${optimazerPrefix}width=800,quality=50,format=webp/${originalImageUrl}`,
			w: 800,
		},
	],
	jpeg: [
		{
			src: `${optimazerPrefix}width=1600,quality=50,format=jpeg/${originalImageUrl}`,
			w: 1600,
		},
		{
			src: `${optimazerPrefix}width=800,quality=50,format=jpeg/${originalImageUrl}`,
			w: 800,
		},
	],
	fallback: [originalImageUrl, fallbackImageUrl],
	placeholder: { dataUri: '', color: '#c5c5c5' },
	blur: false,
}
</script>

<h1>Welcome to Svelte Remote Image</h1>
<p>Display optimized images using CDN or other means.</p>

<div>
	<p>Img</p>
	<Img src={imgSrc} style="max-width: 400px; max-width: 80%;" />
</div>
<div>
	<p>Fallback image</p>
	<Img src={fallImageSrc} style="max-width: 400px; max-width: 80%;" />
</div>
<div>
	<p>Picture</p>
	<Picture {src} style="max-width: 400px; max-width: 80%;" />
</div>
<hr />

<div>
	<p>Picture</p>
	<p>blur: true</p>
	<Picture {src} style="max-width: 400px; width: 100%" />
</div>

<div>
	<p>Picture</p>
	<p>blur: false</p>
	<Picture src={blurFalseSrc} style="max-width: 400px; width: 100%" />
</div>

<a
	href="https://github.com/ocknamo/svelte-remote-image"
	target="_blank"
	rel="noopener noreferrer">github</a
>

<div class="wrapper">
	<p>Set style by CSS global class.</p>
	<Img src={imgSrc} class="child-image" />
</div>

<a
	href="https://github.com/ocknamo/svelte-remote-image"
	target="_blank"
	rel="noopener noreferrer">github</a
>

<style>
	.wrapper :global(.child-image) {
		max-width: 400px; max-width: 80%;
		border-radius: 50px;
	}
</style>
