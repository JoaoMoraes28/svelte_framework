<script>
    import { page } from "$app/stores";
    import src from "$lib/assets/search.png";
    import logPet from "$lib/assets/pedePetLog.png";
    import favIcon from "$lib/assets/favicon-32x32.png";

    let race = $page.url.searchParams.get("race");
    let listDogs = [];

    async function getDog(key) {
        let url = `https://dog.ceo/api/breed/${race}/images`;
        let response = await fetch(url);
        let dogs = await response.json();

        if (dogs.code != 404) {
            setListDogs(dogs);
        } else {
            alert('Nenhuma raça encontrada!')
        }
        
    }

    function setListDogs(dogs) {
        listDogs = dogs;
    }

    getDog();
</script>

<svelte:head>
    <title>Pede Pet | Raça</title>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
        href="https://fonts.googleapis.com/css2?family=Gloria+Hallelujah&family=Kristi&family=Roboto:ital,wght@0,100..900;1,100..900&display=swap"
        rel="stylesheet"
    />
    <link rel="shortcut icon" href={favIcon} type="image/x-icon" />
</svelte:head>

<header>
    <div class="containerHeader">
        <img src={logPet} alt="Logo do Web-Site" />
        <span>Um Web-site para busca Canina</span>
    </div>
</header>

<main>
    <div class="containerUlInput">
        <div class="containerInput">
            <input
                on:keypress={() => {
                    if (event.key == "Enter") {
                        getDog();
                    }
                }}
                bind:value={race}
                type="text"
            />
            <button on:click={getDog}>
                <img {src} alt="Lupa para busca da raça do cachorro" />
            </button>
        </div>
        <ul></ul>
    </div>
    <section>
        {#each listDogs.message as dog}
            <img class="imgDog" src={dog} alt="" />
        {:else}
            <p>Nenhum resultado encontrado!</p>
        {/each}
    </section>
</main>

<style>
    * {
        padding: 0;
        margin: 0;
        box-sizing: border-box;
    }

    :global(body) {
        padding: 0;
        margin: 0;
        width: 100dvw;
        height: 100dvh;
        box-sizing: border-box;
        background-color: #fff6e6;
    }

    ::-webkit-scrollbar {
        width: 10px;
        height: 10px;
    }

    ::-webkit-scrollbar-thumb {
        background: #666666;
        border-radius: 10px;
    }

    ::-webkit-scrollbar-track {
        background: #9999993b;
        border-radius: 10px;
    }

    header {
        width: 100%;
        height: 190px;
        opacity: 1;
        box-shadow: 0px 6px 20px 10px rgba(0, 0, 0, 0.267);
    }

    .containerHeader {
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        align-items: center;
        width: 100%;
        height: 100%;
        background-color: #e4e4e454;
    }

    .containerHeader img {
        width: 120px;
        height: auto;
    }

    .containerHeader span {
        font-family: "Gloria Hallelujah", cursive;
        font-size: 20px;
        font-weight: 500;
    }

    main {
        display: flex;
        flex-direction: column;
        align-items: center;
        padding-top: 50px;
        gap: 40px;
        width: 100vw;
        height: calc(100% - 190px);
    }

    section {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        width: 100%;
        height: calc(100% - 80px);
        gap: 5px;
        padding: 0px 10px 10px 10px;
        overflow: auto;
    }

    .imgDog {
        max-width: 100%;
        height: 90%;
        border-radius: 5px;
        border-style: solid;
        border-color: white;
        border-width: 6px;
        transition: 0.2s ease-in-out;
    }

    .imgDog:hover {
        transform: rotate(0.8deg);
    }

    .containerInput {
        display: flex;
        align-items: center;
        width: 320px;
        height: 40px;
        padding: 0px 5px 0px 5px;
        background-color: white;
        border-radius: 20px;
        box-shadow: 4px 6px 5px 0px rgba(0, 0, 0, 0.267);
    }

    input {
        all: unset;
        width: calc(100% - 40px);
        height: 100%;
        font-size: 20px;
        font-family: "Times New Roman", Times, serif;
        border-top-left-radius: 20px;
        border-bottom-left-radius: 20px;
    }

    button {
        all: unset;
        width: 40px;
        height: 40px;
        border-top-right-radius: 20px;
        border-bottom-right-radius: 20px;
    }

    .containerInput img {
        width: 100%;
        height: 100%;
        border-top-right-radius: 15px;
        border-bottom-right-radius: 15px;
    }

    @media (min-width: 1280px) {
        .containerHeader {
            flex-direction: row;
            justify-content: start;
            padding-left: 60px;
            padding-bottom: 10px;
        }

        span {
            display: flex;
            justify-content: center;
            width: calc(100% - 250px);
        }
    }
</style>
