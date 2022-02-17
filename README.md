[![Netlify Status](https://api.netlify.com/api/v1/badges/5d087050-2a56-457a-82ef-93e2a1a0bbb8/deploy-status)](https://healthc.netlify.app/)
# Health
A Demo Health Center Dashboard

### Deployed

[Dashboard](https://healthc.netlify.app/)

### Installation
- Clone the repo `git clone <repo_url>`
- cd into it `cd health`
- run `npm install` to install all dependencies
- run `npm run dev` to start the development server

### Assumptions

The DEMO_EVENTS data structure doesn't explicitly describe a specific event so I assumed somethings.
I assumed the first three objects represented the `total blood sugar event`, `Average blood sugar events` and the `Events between 70 and 180` for each day due to the date pattern.

- Noticed the data was grouped the data by their time
- Also noticed the 3rd record value for each batch fell with the `70-180` range.

And this pattern was used for the next 3 object consecutively.

```js
  const DEMO_EVENTS = [
      // total blood sugar events (today)
      { value: 100, time: moment() },
      // Average blood sugar events (today)
      { value: 155, time: moment() },
      // Events between 70 and 180 (today)
      { value: 83, time: moment() },

      // total blood sugar events (previous day)
      { value: 211, time: moment().subtract(1, "day") },
      // Average blood sugar events (previous day)
      { value: 138, time: moment().subtract(1, "day") },
      // Events between 70 and 180 (previous day)
      { value: 55, time: moment().subtract(1, "day") },

      // total blood sugar events (2 days ago)
      { value: 183, time: moment().subtract(2, "day") },
      // Average blood sugar events (2 days ago)
      { value: 103, time: moment().subtract(2, "day") },
      // Events between 70 and 180 (2 days ago)
      { value: 98, time: moment().subtract(3, "day") },
  ];

````

