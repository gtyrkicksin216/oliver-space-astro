<script lang="ts">
export let readonly: boolean = true
export let rating: number | null = null

const stars: number[] = [1, 2, 3, 4, 5]
const starClassName = 'material-symbols-outlined'

function matchesRating (position: number): boolean {
	return rating ? rating >= position : false
}

function getClassesForStar (position: number): string {
	return [starClassName, matchesRating(position) && 'm--filled'].join(' ')
}

function handleRating (numberOfStars: number): void {
	if (readonly) return
	console.log(numberOfStars)
}
</script>

<div class="star-rating">
	{#each stars as star}
		<button
			class={getClassesForStar(star)}
			on:click={() => handleRating(star)}
		>star_rate</button>
	{/each}
</div>

<style lang="scss">
.material-symbols-outlined {
	color: #bbb;
	&.m {
		&--filled {
			color: #ffd700;
		}
	}
}
</style>
