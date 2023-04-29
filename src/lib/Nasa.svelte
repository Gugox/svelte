<script>
    import Photo from './Photo.svelte';
    let camera = 0;
    let fetch_data = {};
    let active = false;

    const key = "kipvr3OaKVWw75KeArKIH8FittJVfqSyAuGPpqxK";
    let url = "https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&page=1&camera=" + camera + "&api_key=" + key;

    function search() {
        fetch(url)
        .then((response) => response.json())
        .then((data) => {
            fetch_data = data;
            console.log(fetch_data);
            active = true;
        })
        
    }

    function handleSelect(e) {
        camera = e.target.value;
        url = "https://api.nasa.gov/mars-photos/api/v1/rovers/curiosity/photos?sol=1000&page=1&camera=" + camera + "&api_key=" + key;
        console.log(url);
    }
</script>


<h1>Curiosity Mars Photos</h1>
<div>
    <select on:change={handleSelect}>
        <option value="0">Select camera</option>
        <option value="MAST">MAST</option>
        <option value="FHAZ">FHAZ</option>
    </select>
    <button on:click={search} disabled={camera == 0}>Search</button>
</div>
{#if active}
{#each  fetch_data.photos as e}
<Photo img={e.img_src} desc={e.id}/>
    
{/each}
{/if}



<style>

.container_photo > div {
        display: inline-block;
        margin-right: 20px;
        width: 500px;
        height: 300px;
        background-color: black;
    }

    .container_photo {
        display: inline-block;
        margin-right: 20px;
    }

    img {
        width: 100%;
        height: 100%;
    }

</style>
