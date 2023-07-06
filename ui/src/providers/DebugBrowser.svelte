<script>
    import { debugData } from '../utils/debugData';

	let show = false;
    //EXAMPLE
    
    // debugData([
	// 	{
	// 		action: 'setVisible',
	// 		data: true,
	// 	},
	// ])

	
	// const debugArray = [
	// 	{
	// 		test1: "",
	// 		test2: "",
	// 		test3: "",
	// 		test4: "",
	// 	},
	// 	{
	// 		test1: "",
	// 		test2: "",
	// 		test3: "",
	// 		test4: "",
	// 	},
	// ]

	let options = [
		{
			component: 'Show',
			actions : [
				{
					name: "show",
					action: "setVisible",
					data: true,
				},
				{
					name: "hide",
					action: "setVisible",
					data: false,
				},
			]
		},
		// {
		// 	component: 'Example DebugData',
		// 	actions : [
		// 		{
		// 			name: "setData",
		// 			action: "",
		// 			data: debugArray,
		// 		},
		// 	]
		// },

	]
</script>


<div class="absolute top-0 z-[1000] font-medium uppercase m-4">
	<button class="bg-neutral-800 p-3
	3 font-medium uppercase"
		on:click={() => {
			show = !show;
		}}
	>
	Show
	</button>
	{#if show}
	<div class="w-fit h-fit bg-neutral-700 p-2 ">
		{#each options as option}
		<div class="flex flex-row gap-2 items-center m-1">
			<p class="h-full w-full mr-2">{option.component}</p>
			{#each option.actions as action}
			<button class="bg-neutral-600 p-2"
				on:click={() => {

					if (action.custom == true) {
						action.customFunction();
						return
					}
					debugData([
						{
							action: action.action,
							data: action.data,
						},
					])
				}}
			>
			{action.name}
			</button>
			{/each}
		</div>
		{/each}
	</div>
	{/if}
</div>