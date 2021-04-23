<script>
    export let val;
    export let type;

    export function empty() {
        val = '';
    }
</script>

<input type="text" bind:value={val}>
