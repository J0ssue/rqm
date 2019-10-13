<template>
	<div id="app" class="h-full flex justify-center items-center">
		<main id="quote-box" class="bg-green-500 p-16 rounded">
			<blockquote
				id="text"
				class="bg-gray-200 p-6 rounded"
				v-text="rQuote.content"
			></blockquote>
			<p id="author" class="font-bold text-right mt-2 mb-6">
				author: {{ rQuote.author }}
			</p>
			<div class="flex justify-between">
				<a
					:href="`https://twitter.com/intent/tweet?text=${rQuote.content}`"
					target="_blank"
					class="twitter-share-button bg-blue-500 inline-block text-center text-white uppercase rounded px-6 py-2 hover:bg-blue-600"
					id="tweet-quote"
				>
					Tweet quote</a
				>
				<button
					id="new-quote"
					class="px-6 py-2 rounded bg-black text-white uppercase hover:bg-gray-900"
					@click="getRandomQuote"
				>
					new quote
				</button>
			</div>
		</main>
	</div>
</template>

<script>
	export default {
		name: "app",
		data() {
			return {
				rQuote: {}
			};
		},
		mounted() {
			fetch("https://api.quotable.io/random")
				.then(res => {
					return res.json();
				})
				.then(response => {
					this.rQuote = response;
				});
		},
		methods: {
			getRandomQuote() {
				fetch("https://api.quotable.io/random")
					.then(res => {
						return res.json();
					})
					.then(response => {
						this.rQuote = response;
					});
			}
		}
	};
</script>