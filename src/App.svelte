<script>
    import HowTo from "./HowTo.svelte";
    import Timer from "./Timer.svelte";
    let audio

    function timerEnds(e) {
        audio.play()
    }

</script>


<h1>Handwashing App</h1>


<Timer on:end={timerEnds}/>

<HowTo />

<h3>
    <a href="https://www.who.int/gpsc/clean_hands_protection/en/">
        Picture Source
    </a>
    <a href="https://freesound.org/people/metrostock99/sounds/345086/">
        Sound Source
    </a>
</h3>

<audio bind:this={audio} src="sound.mp3"></audio>


<style>
    h1,h3 {
        text-align: center;
    }
</style>