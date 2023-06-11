## Discord Timestamp
---


```js
// JavaScript

console.log(`<t:${parseInt(new Date() / 1000)}:F>`)

// TypeScript

const Timestamp = new Date().getTime() / 1000;
console.log(`<t:${parseInt(`${Timestamp}`)}:F>`)
```

|   STYLE    |     EXAMPLE OUTPUT     |   DESCRIPTION   |
|------------|------------------------|-----------------|
| t          | `00:00`                | Short Time      |
| T          | `00:00:00`             | Long Time       |
| d          | `01/01/2023`           | Short Date      |
| D          | `1 January 2023`       | Long Date       |
| f          | `1 January 2023 00:00` | Short Date/Time |
| F          | `Sunday, 1 January 2023 00:00` | Long Date/Time
| R          | `6 months ago`         | Relative Time     
