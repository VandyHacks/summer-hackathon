<script>
let schedule = [
  {
    time: "Jul 10,  7:45pm - 8pm",
    event: "Opening Ceremony",
  },
  {
    time: "Jul 10,  8pm",
    event: "Hacking Starts",
  },
  {
    time: "Jul 10,  8:30pm - 9:30pm",
    event: "Google Firebase talk by Andrea Wu",
    link: "https://www.twitch.tv/vandyhacks",
  },
  {
    time: "Jul 10,  10pm - 11pm",
    event: "Lemon Bar Making",
  },
  {
    time: "Jul 10,  10:30pm - 11:15pm",
    event: "Wellness",
  },
  {
    time: "Jul 11,  10am - 11am",
    event: "Open-saurus Rex Workshop: How to Contribute to Open Source ",
    link: "https://vanderbilt.zoom.us/j/98387736601"
  }, 
  {
    time: "Jul 11,  11am - 12pm",
    event: "SlackBot Workshop ",
    link: "https://www.twitch.tv/vandyhacks",
  },
  {
    time: "Jul 11,  12pm - 1pm",
    event: "MLH Mini Event",
  },
  {
    time: "Jul 11,  1pm - 2pm",
    event: "Skribbl.io",
  }, 
  {
    time: "Jul 11,  2:30pm - 3pm",
    event: "Zumba",
  }, 
  {
    time: "Jul 11,  4pm - 5pm",
    event: "Typing Race",
  }, 
  {
    time: "Jul 11,  7pm - 8pm",
    event: "Lightning Talks",
  },
  {
    time: "Jul 12,  8am",
    event: "Hacking Ends",
  }, 
  {
    time: "Jul 12, 8am - 9am",
    event: "Submit to Devpost!",
  },
  {
    time: "Jul 12,  9am - 11:30am",
    event: `Judging Block`,
  }, 
  {
    time: "Jul 12,  11:45am - 12pm",
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


a {
  color: #bbbbc4;
  text-decoration: none;
  -o-transition: 0.5s;
  -ms-transition: 0.5s;
  -moz-transition: 0.5s;
  -webkit-transition: 0.5s;
  transition: 0.5s;
}

a:hover {
  color: #ffdb73;
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
        {#if item.link}
          <td class="link"> <a href={item.link} target="_blank" rel="noreferrer"> {item.event} - <txt style="color:#ffdb73">link</txt></a></td>
        {:else}
        <td>{item.event}</td>
        {/if}
      </tr>
    {/each}
  </tbody>
</table>


</schedule-table>
