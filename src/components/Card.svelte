<script>
  export let indicator = "green";
  export let unit = "events";
  export let previousDay = "";
  export let today = "";
  export let label = "";
</script>

<div class="card">
  <div class="row1">
    <span class="icon" />
    <h3>{label}</h3>
  </div>

  {#if today}
  <div class="row2">
    <h1><span class={`indicator ${indicator}`} /> {today}</h1> <span class="unit">{unit}</span>
  </div>
  {:else}
  <div class="no-events">
    <h1 class="no-data">Not enough events</h1>
  </div>
  {/if}

  {#if previousDay}
  <div class="row3">
    <span>Previous day -</span>
    <span class={`prev-day ${indicator}`}>{previousDay}</span>
  </div>
  {/if}
</div>

<style>
  .card {
    position: relative;
    flex-grow: 1;
    padding: 10px;
    box-shadow: 0px 5px 10px rgba(0, 0, 0, 0.2);
    border-radius: 10px;
    max-height: 130px;
    min-height: 100px;
    max-width: 400px;
    min-width: 350px;
  }

  .row1 {
    display: flex;
    align-items: center;
    justify-content: flex-start;
  }

  .row1 .icon {
    display: inline-block;
    width: 65px;
    height: 50px;
    background-image: url("/assets/event-sprite.png");
    background-repeat: no-repeat;
    filter: contrast(0);
    opacity: 0.5;
    position: absolute;
    top: -5px;
    left: -10px;
    transform: scale(0.4);
  }

  .row1 h3 {
    margin-left: 25px;
  }

  .row2 {
    display: flex;
    align-items: flex-end;
    justify-content: flex-end;
  }

  .row2 h1 {
    position: relative;
    font-weight: 500;
  }

  .row2 .unit {
    font-size: 1em;
    margin-bottom: 8px;
    margin-left: 5px;
  }

  .row2 .indicator {
    display: inline-block;
    width: 8px;
    height: 8px;
    border-radius: 10px;
    position: absolute;
    left: -15px;
    bottom: 21px;
  }

  .row2 .indicator.green {
    background-color: var(--green);
  }
  .row2 .indicator.blue {
    background-color: var(--blue);
  }
  .row2 .indicator.orange {
    width: 48px;
    height: 48px;
    border-radius: 0;
    background: url("/assets/status-sprite.png") no-repeat;
    transform: rotate(180deg) scale(0.3);
    position: absolute;
    left: -35px;
    bottom: 0;
  }

  .row3 {
    display: flex;
    align-items: center;
    justify-content: flex-end;
    gap: 5px;
  }

  .row3 span {
    color: var(--dark-grey);
  }

  .row3 .prev-day.green {
    color: var(--green);
    font-weight: bold;
  }
  .row3 .prev-day.blue {
    color: var(--blue);
    font-weight: bold;
  }
  .row3 .prev-day.orange {
    color: var(--orange);
    font-weight: bold;
  }


  .no-events {
    padding: 15px 0;
  }

  .no-data {
    color: var(--light-grey);
    font-size: 2em;
    font-weight: 500;
    text-align: end;
  }
</style>
