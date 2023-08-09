<script>
    let details = {
        Name: "",
        Email: "",
        Phone: "",
        Address: "",
    };

    let save = false;
    let show = false;
    let edit = false;

    function changeSave() {
        save = !save;
        changeEdit();
        show = true;
    }

    function changeEdit() {
        edit = !edit;
        show = false;
    }
</script>

{#if show && details.Name && details.Email && details.Phone && details.Address}
    <div>
        <p>Full Name: {details.Name}</p>
        <p>Email: {details.Email}</p>
        <p>Phone Number: {details.Phone}</p>
        <p>Address: {details.Address}</p>
    </div>
{:else}
    <div>
        <p>Personal Details:</p>
    </div>
{/if}

{#if !edit}
    <button on:click={changeEdit}>Edit</button>
{/if}
{#if edit}
    {#each Object.entries(details) as [field] (field)}
        <div>
            <label for={field}>{field}:</label>
            <input type="text" id={field} bind:value={details[field]} />
        </div>
    {/each}
    <button on:click={changeSave}>Save</button>
{/if}
