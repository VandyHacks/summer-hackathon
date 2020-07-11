<script>
// Set the date we're counting down to
let countDownDate = new Date("July 12, 2020 08:00:00").getTime();

// Get today's date and time
let now = new Date().getTime();
setInterval(() => {now = new Date().getTime();}, 1000)
$: distance = countDownDate - now;

// Time calculations for days, hours, minutes and seconds
$: days = distance >= 0 ? Math.floor(distance / (1000 * 60 * 60 * 24)) : 0;
$: hours =  distance >= 0 ? Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60)): 0;
$: minutes = distance >= 0 ?  Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60)): 0;
$: seconds = distance >= 0 ? Math.floor((distance % (1000 * 60)) / 1000): 0;

</script>

<style>

.figure {
  color: #ffdb73;
  font-size: 4rem;
  text-align: center;
  margin-top: 2rem;
}


@media (max-width: 550px) {
    .figure {
     margin-top: 0rem;
     text-align: center;

    } 
  }
</style>

<countdown>
  <h2 class="figure">
    {days}:
    {hours}:
    {minutes}:
    {seconds}
  </h2>
</countdown>