<script>
let schedule = [
  {
    time: "Jul 10,  7:45pm",
    event: "Opening Ceremony",
  },
  {
    time: "Jul 10,  8pm",
    event: "Hacking Starts",
  },
  {
    time: "Jul 10,  10pm - 11pm",
    event: "Lemon Bar Making",
  },
  {
    time: "Jul 10,  10:30pm - 11:30pm",
    event: "Wellness",
  }, 
  {
    time: "Jul 11,  12am - 1am",
    event: "Quiplash",
  }, 
  {
    time: "Jul 11,  10am - 11am",
    event: "Open-Saurus Rex",
  }, 
  {
    time: "Jul 11,  11am - 12pm",
    event: "SlackBot Workshop",
  }, 
  {
    time: "Jul 11,  1pm - 2pm",
    event: "Skribbl.io",
  }, 
  {
    time: "Jul 11,  2:30pm - 3:30pm",
    event: "Zumba",
  }, 
  {
    time: "Jul 11,  4pm - 5pm",
    event: "Typing Race",
  }, 
  {
    time: "Jul 12,  8am",
    event: "Hacking Ends",
  }, 
  {
    time: "Jul 12,  8:15am - 10:15am",
    event: `Judging Block`,
  }, 
  {
    time: "Jul 12,  10:15am - 10:45am",
    event: "Closing Ceremony",
  }, 
];
</script>

<style>
table {
  color: #bbbbc4;
}

td, th {
  border-color: #555560;
}

/* .makeBold {
  font-weight: bold;
} */
/* change line color */
</style>

<schedule-table>
<!-- TODO update schedule (could use function loop to generate table entris here) -->
<table class="u-full-width">
  <thead>
    <tr>
      <th>Time (Central Time Zone)</th>
      <th>Event</th>
    </tr>
  </thead>
  <tbody>
    {#each schedule as item}
      <tr>
        <td>{item.time}</td>
        <td>{item.event}</td>
      </tr>
    {/each}
  </tbody>
</table>


</schedule-table>
