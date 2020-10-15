<script>
    import ProgressBar from "../components/ProgressBar.svelte";

    const totalSeconds = 20;
    let secondLeft = totalSeconds;
    let isRunning = false;

    $: progress = ((totalSeconds - secondLeft) / totalSeconds) * 100;
    function startTimer() {
        let timer = setInterval(() => {
            isRunning = true;
            secondLeft -= 1;
            if (secondLeft == 0) {
                clearInterval(timer);
                isRunning = false;
                secondLeft = totalSeconds;
            }
        }, 1000);
    }
</script>

<style>
    h2 {
        margin: 0;
    }
    .start {
        background-color: maroon;
        width: 100%;
        margin: 10px 0;
    }
    .start[disabled] {
        background-color: rgb(194, 194, 194);
        cursor: not-allowed;
    }
</style>

<div bp="grid">
    <h2 bp="offset-5@md 4@md 12@sm">Second Left : {secondLeft}</h2>
</div>
<ProgressBar {progress} />

<div bp="grid">
    <button
        on:click={startTimer}
        disabled={isRunning}
        bp="offset-5@md 4@md 12@sm"
        class="start">Start</button>
</div>
