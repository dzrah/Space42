<script>
	let { class: className = '', children, id: idName = '' } = $props();
</script>

<div class="w-full max-w-6xl mx-auto px-4 sm:px-8 lg:px-16 {className} {idName}">
	{@render children()}
</div>
