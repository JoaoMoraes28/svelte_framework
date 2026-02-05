<script>
    import { goto } from "$app/navigation";
    import src from "$lib/assets/search.png";
    import logPet from "$lib/assets/pedePetLog.png";

    let raceDog;

    function goPageDog() {
        goto(`/pageDog?race=${raceDog}`);
    }
</script>

<svelte:head>
    <title>Busca Dog</title>
    <link rel="preconnect" href="https://fonts.googleapis.com" />
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
    <link
        href="https://fonts.googleapis.com/css2?family=Gloria+Hallelujah&family=Kristi&family=Roboto:ital,wght@0,100..900;1,100..900&display=swap"
        rel="stylesheet"
    />
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
            <input bind:value={raceDog} type="text" />
            <button on:click={goPageDog}>
                <img {src} alt="Lupa para busca da raça do cachorro" />
            </button>
        </div>
        <ul></ul>
    </div>
</main>
<footer></footer>

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
        justify-content: center;
        padding-top: 50%;
        width: 100vw;
        height: calc(100% - 190px);
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
</style>
