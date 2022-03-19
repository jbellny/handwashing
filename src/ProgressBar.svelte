<script>
    export let barWidth = 0
</script>

<div bp='grid'>
    <div bp="offset-4@md 4@md 12@sm" class="progress-container">
        <div 
            class="progress-bar" 
            style="width: {barWidth}%">
            <span class="sr-only">{barWidth}%</span>
        </div>
    </div>
</div>

<style>
    .progress-container {
        margin: 20px 0;
        border: solid rgba(194,194,194);
    }

    .progress-bar {
        height: 30px;
        background-color: rgb(77,199,55);
    }
</style>