<script>
	let facts = $state([])

	async function fetch_new_fact() {
		try {
			const result = await fetch("https://catfact.ninja/fact")
			if (result.ok) {
				const data = await result.json()
				facts.push(data.fact)
			} else {
				alert("Oh no it broke.")
			}
		} catch {
			alert("Oh no it super-broke.")
		}
	}
</script>


<ul>
	{#each facts as fact}
		<li>{fact}</li>
	{/each}
</ul>
<button onclick={fetch_new_fact}>Get a new fact</button>
