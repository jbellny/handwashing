<script>
    import ProgressBar from './ProgressBar.svelte'
    import { createEventDispatcher } from 'svelte'

    const totalSeconds = 20
    let secondsLeft = totalSeconds
    let isRunning = false
    $: barWidth = (totalSeconds-secondsLeft)/totalSeconds*100

    const dispatch = createEventDispatcher()

    function startTimer() {
        if (isRunning) return
        isRunning = true
        const timerOn = setInterval(() => {
            secondsLeft --
            if (secondsLeft == 0) {
                clearInterval(timerOn)
                dispatch('end')
                isRunning = false
                secondsLeft = totalSeconds
            }
        }, 1000);
    }

</script>
<div bp='grid'>
    <h2 
        bp="offset-5@md 4@md 12@sm">
        Seconds Left: {secondsLeft}
    </h2>
</div>

<ProgressBar {barWidth}/>

<div bp='grid'>
    <button disabled={isRunning} on:click={startTimer} bp="offset-5@md 4@md 12@sm" class="start">
        Start
    </button>
</div>

<style>
    h2 {
        margin: 0;
    }
    .start {
        background-color: rgb(154,73,73);
        width: 100%;
        margin: 10px 0;
    }

    .start[disabled] {
        background-color: gray;
        color: darkgray;
        cursor: not-allowed;
    }
</style>