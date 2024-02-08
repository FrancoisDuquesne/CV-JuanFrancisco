<script>
	let info = {
		name: 'Juan Francisco',
		surname: 'Araujo Bayas',
		email: 'juanfran@live.com',
		phone: '+593 994189130',
		linkedin: 'https://www.linkedin.com/in/juan-francisco-araujo-bayas-57b170126/',
		github: 'https://github.com/juan15-fran'
	};

	let className = '';
	export { className as class };
</script>

<section class={`space-y-6 ${className || ''}`}>
	<p class="text-7xl">{info.name} {info.surname}</p>

	<p class="text-2xl font-light">
		MSc, Master’s degree in Business Engineering, specialized in Supply Chain Management and
		Strategic Procurement
	</p>

	<div class="flex flex-col gap-2">
		<p>
			<span class="text-stone-500">mail:</span>
			<a href="mailto:{info.email}">{info.email}</a>
		</p>
		<p><span class="text-stone-500">tel:</span> {info.phone}</p>
	</div>
</section>
