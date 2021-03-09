<script>
    import Sound from './Sound.svelte';

    const sounds = [
        {
            letra: 'A',
            nombre: 'Clap',
            sound: 'sounds/clap.wav',
        },
        {
            letra: 'S',
            nombre: 'HiHat',
            sound: 'sounds/hihat.wav',
        },
        {
            letra: 'D',
            nombre: 'Kick',
            sound: 'sounds/kick.wav',
        },
    ];
</script>

<h1>Hola deBakatas</h1>

<!--
Crear info casilla ✅
- Letra (Presione)
- Nombre
- Sonido
 -->

<div>
    {#each sounds as sound}
        <Sound letra={sound.letra} sound={sound.sound} nombre={sound.nombre} />
    {/each}
</div>

<style>
    div {
        display: flex;
        justify-content: space-around;
    }
</style>
