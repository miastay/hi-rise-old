<script>
    import { Dialog } from "svelte-materialify";

    export let color = "#ffeedd";
    export let name = "Color"

    let dialogOpen = false;

</script>

<div class="picker" role="button" on:click={() => dialogOpen = true}>
    <div class="color" style={`background: ${color}`}/>
    <span>{name}</span>
</div>
<Dialog class="pa-4 text-center" bind:active={dialogOpen}>
    <input type="text" placeholder="hex value" bind:value={color} on:blur={() => dialogOpen = false} on:keydown={(event) => {
        if (event.key === 'Enter') {
            dialogOpen = false;
        }
      }}/>
</Dialog>

<style lang="scss">
    .picker {
        display: flex;
        flex-direction: row;
        gap: 0.5rem;
        align-items: center;
        &:active {
            .color {
                outline: solid 2px white;
                outline-offset: -1px;
                border: solid 3px black;
                transition: all 0.1s ease;
            }
        }
        .color {
        width: 25px;
        height: 25px;
        border-radius: 15px;
        }
    }
</style>

