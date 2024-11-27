<script lang="ts">
    import "../src/css/calendar.css"

    // stores the selected card and controls the modal visibllity 
    let selectedCard:any = null
    let showModal = false

    // Populating the days 
    let days = []
    for (let i = 1; i <= 24; i++) {
        days.push(i)
    }

    //handle card click function
    const handleCardClick = (day: any) => {
        selectedCard = day
        showModal = true
    }

    //close the modal function
    const closeModal = () => {
        showModal = false
    }
</script>

<div class="calendar">
    {#each days as day}
        <div class="day-card" on:click={() => handleCardClick(day)}>
            Day {day}
        </div>
    {/each}
</div>

{#if showModal}
    <div class="modal" on:click={closeModal}>
        <div class="modal-content" on:click|stopPropagation>
            <span class="close" on:click={closeModal}>&times;</span>
            <img
                id="modal-image"
                src={`https://placehold.co/300x300?text=Day+${selectedCard}`}
                alt={`Day ${selectedCard}`}
            />
            <p id="modal-text">Day {selectedCard} - Surprise!</p>
        </div>
    </div>
{/if}
