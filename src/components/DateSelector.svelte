<script>
  import moment from "moment";

  export let prevBtnDisable = false;
  export let nextBtnDisable = false;
  export let date = "";
  export let onNext = () => {};
  export let onPrev = () => {};

  let defaultDate = moment();

  $: newDate = date || defaultDate;

  const handleBack = () => {
    onPrev();
    defaultDate = defaultDate.subtract(1, "day");
  };

  const handleNext = () => {
    onNext();
    defaultDate = defaultDate.add(1, "day");
  };
</script>

<div class="date-selector-container">
  <h2>
    {`${newDate?.format?.("ddd")}, ${newDate?.format?.("D")} ${newDate?.format?.(
      "MMM"
    )} ${newDate?.format?.("YYYY")}`}
  </h2>
  <div class="btn-container">
    <button
      on:click={handleBack}
      disabled={prevBtnDisable}
      class="previous"
      type="button"><span /></button
    >
    <button on:click={handleNext} disabled={nextBtnDisable} class="next" type="button"
      ><span /></button
    >
  </div>
</div>

<style>
  .date-selector-container {
    display: flex;
    align-items: center;
    margin: 30px 0;
    position: relative;
  }

  .date-selector-container h2 {
    color: var(--dark-grey);
    font-size: 2rem;
    font-weight: 500;
  }

  .btn-container {
    display: flex;
    position: absolute;
    left: 300px;
  }

  @media (max-width: 768px) {
    .btn-container {
      display: flex;
      position: absolute;
      left: 250px;
  }
  }

  button {
    position: relative;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  button:hover::after {
    content: "";
    position: absolute;
    width: 200px;
    height: 200px;
    border-radius: 100px;
    background-color: rgba(0, 0, 0, 0.1);
  }

  button span {
    display: inline-block;
    width: 65px;
    height: 60px;
    background-image: url("/assets/arrow-sprite.png");
    background-repeat: no-repeat;
    filter: contrast(0);
    opacity: 0.5;
  }

  .previous {
    transform: rotate(-90deg) scale(0.3);
  }

  .next {
    transform: rotate(90deg) scale(0.3);
  }
</style>
