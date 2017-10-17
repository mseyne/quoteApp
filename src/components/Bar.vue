<template>
<div>
    <h6 class="mt-3">Quote Added</h6>
    <div class="progress">
        <div class="progress-bar" role="progressbar" :style="updateBarWidth" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100"> {{ nbQuotes.now }} / {{ nbQuotes.max }} </div>
    </div>
</div>
</div>
</template>

<script>
    export default {
        props:['nbQuotes'],
        computed: {
            updateBarWidth: function() {
                const max = this.nbQuotes.max;
                const now = this.nbQuotes.now;
                if (now > 0) {
                    const percent = Math.floor((now/max)*100);
                    // console.log('bar width updated', max, now, percent);
                    return `height: 20px; width: ${percent}%; font-weight: bold; line-height: 20px;`
                } else {
                    return `color:#e9ecef; width: 0%; height: 20px;`
                }
            }
        }
    }
</script>

<style scoped>

/* .progress-bar {
    font-weight: bold;
    line-height: 20px;
} */

</style>
