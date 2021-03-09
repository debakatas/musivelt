<script>
    import { onMount } from 'svelte';
    import App from './App.svelte';

    // Props (Vienen del padre)
    export let letra;
    export let nombre;
    export let sound;

    // Variable vacia (Elemento HTML)
    let audio;
    let activado = false;

    // funcion de reproducir
    function playMusic() {
        // agregar una clase
        // Promesa
        activado = true;
        audio.play();
    }

    function removeClass() {
        activado = false;
    }

    onMount(function () {
        window.addEventListener('keydown', function (evento) {
            if (evento.key === letra.toLowerCase()) {
                playMusic();
            }
        });
    });
</script>

<!-- Cuando el usuario haga click -->
<!-- corra la funcion -->
<!-- conectar con esa clase -->
<div on:click={playMusic} on:mouseenter={playMusic} class:activado>
    <kbd>
        {letra}
    </kbd>

    {#if activado}
        <span>{nombre}</span>
    {:else}
        <span>???</span>
    {/if}
    <!-- this -->
    <!-- Cuando se cree este componente -->
    <!-- guardeme el element HTML en audio -->
    <audio src={sound} bind:this={audio} on:ended={removeClass} />
</div>

<style>
    div {
        border: 2px solid #151515;
        background: rgba(0, 0, 0, 0.5);
        color: white;
        padding: 30px;
        border-radius: 20px;
    }

    .activado {
        border-color: yellowgreen;
        transform: scale(1.2);
    }
</style>
