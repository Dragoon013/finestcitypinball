<script>
	let cart = [];
	let isModalOpen = false;
	/**
	 * @type {{id: string, name: string, status: string, image: string, createdAt: string}[]}
	 */
	export let machines;
	/**
	 * @type {number}
	 */
	export let duration;

	/**
	 * @param {string | number | Date} timestamp
	 * @param {undefined} [timeOnly]
	 */
</script>

<div class="flex items-center justify-between mb-4">
	<div class="space-y-1">
		<h2 class="text-xl font-semibold">Machines</h2>
		<p class="text-sm text-gray-500">
			Fetched {machines.length} machines in {duration ? duration : 'unknown'} ms
		</p>
	</div>
</div>
<div
	class="p-10 grid grid-auto-rows grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-9"
>
	{#each machines as machine (machine.id)}
		<div class="card overflow-hidden min-w-32 bg-base-100 shadow-lg">
			<figure><img src={machine.image} alt={machine.name} /></figure>
			<div class="card-body">
				<h2 class="card-title">{machine.name}</h2>
				<p>This is a description about a pinball machine</p>
				<div class="card-actions justify-end">
					<button on:click={() => (isModalOpen = true)} class="btn btn-primary">Reserve Now</button>
					<div class="modal" class:modal-open={isModalOpen}>
						<div class="modal-box w-11/12 max-w-5xl">
							<!-- Calendly inline widget begin -->
							<form method="dialog">
								<button on:click={() => (isModalOpen = false)} class="btn btn-sm btn-circle btn-ghost absolute right-2 top-2">✕</button>
							  </form>
							<div
								class="calendly-inline-widget"
								data-url="https://calendly.com/jacob-a-teal/pinball-rental?hide_landing_page_details=1"
								style="min-width:320px; height:600px; padding:20px;"
							/>
							<script
								type="text/javascript"
								src="https://assets.calendly.com/assets/external/widget.js"
								async
							></script>
							<!-- Calendly inline widget end -->
						</div>
					</div>
				</div>
			</div>
		</div>
	{/each}
</div>

<style>
	.card-body {
		color: white;
	}
</style>
