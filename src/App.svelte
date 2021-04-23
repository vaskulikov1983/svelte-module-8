<script>
    import CustomInput from "./CustomInput.svelte";
    import Toggle from "./Toggle.svelte";

    let val = "Max";
    let selectedOption = 1;
    let price;

    $: console.log(val);
    $: console.log(selectedOption);
    $: console.log(price);

    const changeValue = (evt) => {
        val = evt.target.value;
    }
</script>

<!-- <input type="text" bind:value={val}> -->

<CustomInput type="text" bind:val={val} />
<Toggle bind:chosenOption={selectedOption}/>

<input type="number" bind:value={price}>
