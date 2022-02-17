<script>
  import moment from "moment";

  import Header from "./components/Header.svelte";
  import Card from "./components/Card.svelte";
  import DateSelector from "./components/DateSelector.svelte";
  import PublicLayout from "./Layout/Public.svelte";

  const DEMO_EVENTS = [
    [
      { value: 100, time: moment() },
      { value: 155, time: moment() },
      { value: 83, time: moment() },
    ],
    [
      { value: 211, time: moment().subtract(1, "day") },
      { value: 138, time: moment().subtract(1, "day") },
      { value: 55, time: moment().subtract(1, "day") },
    ],
    [
      { value: 183, time: moment().subtract(2, "day") },
      { value: 103, time: moment().subtract(2, "day") },
      { value: 98, time: moment().subtract(3, "day") },
    ],
  ];

  let currentIndex = 0;
  let previousData = null;
  let currentData = DEMO_EVENTS[currentIndex];

  const handleDateChange = (direction) => {
    previousData = currentData;
    currentData = DEMO_EVENTS[currentIndex + direction];
    currentIndex = currentIndex + direction;
  };
</script>

<main>
  <Header />
  <PublicLayout>
    <DateSelector
      onNext={() => handleDateChange(-1)}
      onPrev={() => handleDateChange(+1)}
      date={currentData?.[0]?.time}
    />
    <section class="card-wrapper">
      <Card
        label="Total blood sugar events"
        indicator="blue"
        unit="events"
        today={currentData?.[0]?.value}
        previousDay={previousData?.[0]?.value}
      />
      <Card
        label="Average blood sugar"
        indicator="orange"
        unit="mg/dL"
        today={currentData?.[1]?.value}
        previousDay={previousData?.[1]?.value}
      />
      <Card
        label={`Events between 70 and 180`}
        indicator="green"
        unit="%"
        today={currentData?.[2]?.value}
        previousDay={previousData?.[2]?.value}
      />
    </section>
  </PublicLayout>
</main>

<style>
  main {
    max-width: 1440px;
    margin: 0 auto;
  }

  .card-wrapper {
    display: flex;
    justify-content: space-between;
    flex-wrap: wrap;
    gap: 30px;
    margin-bottom: 50px;
  }
</style>
