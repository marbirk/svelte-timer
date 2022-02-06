<script>
    let changeColor = false;
</script>

<div class={`ring ${changeColor && 'ending'}`}>
    <svg width="518" height="518" viewBox="0 0 518 518">
        <circle stroke-width="9px" x="0" y="y" cx="259" cy="259" r="254" />
    </svg>
</div>

<style>
	.ring {
        position: absolute;
        left: 0;
        stroke: #09A65A;
        top: 0;
        z-index: 1;
    }
    .ring.ending circle {
        stroke: #900A0A;
    }
</style>