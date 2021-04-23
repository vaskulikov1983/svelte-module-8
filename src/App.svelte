<script>
    import CustomInput from "./CustomInput.svelte";
    import Toggle from "./Toggle.svelte";
    import {validation} from "./validation.js";

    let val = "Max";
    let selectedOption = 1;
    let price;
    let agree = false;
    let favColor = ["Green"];
    let singleFavColor = 'red';
    let usernameInput;
    let someDiv;
    let customInput;
    let enteredEmail = '';
    let isValid = false;

    $: console.log(val);
    $: console.log(selectedOption);
    $: console.log(price);
    $: console.log(agree);
    $: console.log(favColor);
    $: console.log(singleFavColor);
    $: console.log(customInput);

    $: if (validation(enteredEmail)) {
        isValid = true;
    } else {
        isValid = false;
    }

    const changeValue = (evt) => {
        val = evt.target.value;
    }

    const saveData = () => {
        // console.log(document.querySelector("#username").value);
        // console.log(usernameInput.value);
        // console.dir(usernameInput);
        console.dir(someDiv);
        customInput.empty();
    }
</script>

<style>
    .invalid {
        border: 1px solid red;
    }
</style>

<!-- <input type="text" bind:value={val}> -->

<CustomInput type="text" bind:val={val} bind:this={customInput}/>

<Toggle bind:chosenOption={selectedOption}/>

<input type="number" bind:value={price}>
<h1>What is your favorite color?</h1>
<!-- <label>
    <input type="checkbox" bind:checked={agree}>
    Do you agree?
</label> -->

<label>
    <input type="checkbox" name="colors" value="Red" bind:group={favColor}>
    Red
</label>
<label>
    <input type="checkbox" name="colors" value="Green" bind:group={favColor}>
    Green
</label>
<label>
    <input type="checkbox" name="colors" value="Blue" bind:group={favColor}>
    Blue
</label>

<select bind:value={singleFavColor}>
    <option value="green">Green</option>
    <option value="red">Red</option>
    <option value="blue">Blue</option>
</select>

<hr>

<input type="text" bind:this={usernameInput}>
<button on:click="{saveData}">Save</button>

<div bind:this={someDiv}></div>

<hr>

<form on:submit|preventDefault>
    <input type="email" bind:value={enteredEmail} class={isValid ? '' : 'invalid'}>
    <button type="submit" disabled={!isValid}>Save</button>
</form>
