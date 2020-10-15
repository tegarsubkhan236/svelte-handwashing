<script>
    import Timer from "./components/Timer.svelte";
    import HowTo from "./components/HowTo.svelte";
    let audio;
    function timerEnds(e) {
        audio.play();
    }
</script>

<style>
    h1 {
        text-align: center;
    }
</style>

<h1>Handwashing App</h1>
<Timer on:end={timerEnds} />
<HowTo />

<audio bind:this={audio}>
    <source src="sound.wav" />
</audio>
