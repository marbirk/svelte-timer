<script>
    import GearIcon from './GearIcon.svelte';
    import { onDestroy, onMount } from 'svelte';
    import { a } from './stores.js';

    let isActive = false;
    let time = $a;
    let minutes = getMinutes();
    let seconds = getSeconds();
    let interval;
    
    function handleClick() {
        isActive = !isActive
        isActive ? startTimer() : stopTimer();
    }

    function startTimer() {
        interval = setInterval(() => decrementTime(), 1000);
    }

    function stopTimer() {
        clearInterval(interval);
    }

    function getMinutes() {
        return formatTimeStrings(Math.floor((time % 3600) / 60));
    }

    function getSeconds() {
        return formatTimeStrings(time % 60);
    }

    function formatTimeStrings(time) {
        let timeString = time.toString();
        return timeString.length === 1 ? '0' + timeString : timeString;
    }

    function decrementTime() {
        if (time === 0) {
            stopTimer();
            return alert('Time is up!');
        }
        time--;
        minutes = getMinutes();
        seconds = getSeconds();
    }

    onDestroy(() => {
		stopTimer();
	});
</script>

<div class="timer">
    <div class="time">
      <div class="minutes">
        <input type="text" value={minutes} disabled />
      </div>
      <div class="colon">:</div>
      <div class="seconds">
        <input type="text" value={seconds} disabled />
      </div>
    </div>
    <button on:click={handleClick} class="start">{isActive ? 'stop' : 'start'}</button>
    <button class="settings">
      <GearIcon/>
    </button>
</div>

<style>
	/* inner circle */
    .timer {
        align-items: center;
        background: radial-gradient(71.4% 71.4% at 51.7% 28.6%, #3A393F 0%, #17171A 100%);
        border-radius: 50%;
        box-shadow: inset 0px 0px 114px rgba(0, 0, 0, 0.45);
        color: white;
        display: flex;
        flex-direction: column;
        height: 500px;
        justify-content: center;
        position: relative;
        width: 500px;
        z-index: 2;
    }

    /* actual time */
    .time {
        display: flex;
        font-family: "bebas";
        font-size: 196px;
        margin: 30px auto;
        position: relative;
        top: 30px;
    }

    input[type="text"] {
        border: 0;
        border-bottom: 1px dashed white;
        background: none;
        color: white;
        font-family: "bebas";
        font-size: 196px;
        height: 170px;
        width: 150px;
        text-align: center;
        outline: none;
    }

    input[type=text]:disabled {
        border-bottom: none;
    }

    .start {
        cursor: pointer;
        font-family: 'Montserrat', sans-serif;
        font-size: 16px;
        letter-spacing: 10px;
        line-height: 20px;
        background: none;
        color: white;
        opacity: .5;
        border: none;
        text-transform: uppercase;
        margin-bottom: 20px;
    }

    .start:hover {
        opacity: 1;
    }

    .settings {
        border: none;
        background: none;
        cursor: pointer;
        opacity: 0.3;
    }

    .settings:hover {
        opacity: 1;
    }
</style>