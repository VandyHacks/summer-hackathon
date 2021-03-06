<script>
  // for svg and page animation effect
  import { draw, fade, fly } from "svelte/transition";
  import { expand } from "./custom-transitions.js";
  import FAQ from "./faq.svelte";
  import Schedule from './schedule.svelte';
  import Countdown from './countdown.svelte';
  import Links from './links.svelte';
  import Cards from './cards.svelte';

  // type writer effect
  function typewriter(node, { delay = 0, speed = 70 }) {
    const valid =
      node.childNodes.length === 1 &&
      node.childNodes[0].nodeType === Node.TEXT_NODE;

    if (!valid) {
      throw new Error(
        `This transition only works on elements with a single text node child`
      );
    }

    const text = node.textContent;
    const duration = text.length * speed;

    return {
      delay,
      duration,
      tick: t => {
        const i = ~~(text.length * t);
        node.textContent = text.slice(0, i);
      }
    };
  }

  // placeholder url for all links in the page
  const vhPlaceholderURL = "https://vandyhacks.org/";

  const introText = "VandyHacks is Vanderbilt’s student-run hackathon, where participants from all over the country create innovative and meaningful projects over the course of 36 hours. This year, our hackathon will be held virtually on July 10th-12th, meaning you can participate from the comfort of your own home! Come learn new topics with recorded workshops ranging from open source code to creating your own SlackBot. Meet and unwind with other fellow hackers with a round of Skribbl.io or virtual baking. Your project also has the chance to win some of our cool prizes! "

  const nonProfitIntro = "As part of a summer externship opportunity, VandyHacks has partnered with non-profit organizations to give hackers the option of creating projects for social good. While hackers will be judged on the progress made during the weekend, the projects will continue after the hackathon and through the rest of summer. By partnering with a company and building meaningful software, hackers can gain valuable real-world experience. If you're interested, you can check out our partners below or read more about the "
  const npoGuidelineLink = ''
  const nonProfitIntroBold = "Also, you are not required to work on one of these projects"
  const nonProfitIntroCont = " - in fact, you can compete for the first and second place prizes which are completely separate, and your project can be based on anything."
  
  // define faq items
  const questionSetLeft = [
    {
      question: "What is a hackathon?",
      answer:
        "Hackathons are events where students from across the country come together for a weekend of innovation and creativity. Participants have 36 hours to create anything that shows off their creativity and passion for development. You may choose any platform, programming language, or format to show your stuff. You can even present a storyboard or idea; there’s no end to the possibilities!"
    },
    {
      question: "How does registration work?",
      answer:
        "Since this is an online event, we want to open registration to anyone that is interested. If you're curious, email us for more info at info@vandyhacks.org."
    },
    {
      question: "What if I've never been to a hackathon?",
      answer:
        "Not to worry! A few weeks before the event, you’ll receive an email with a link to our hacker guide, which will contain all the information you need to make the most out of your weekend. During the event, the VandyHacks Team will be around to help answer any questions. As always, feel free to email us at info@vandyhacks.org, or reach out on Discord."
    },
    {
      question: "What do I need?",
      answer:
        "Some kind of device you can write code on, and an internet connection!"
    },
    {
      question: "How are teams formed? Do I need a team?",
      answer:
        "Teams are formed in the #team-finding channel–feel free to find people that share interests, and get building. We'll also provide a virtual space to meet teams. However, teams are not required, so feel free to work individually."
    },
    {
      question: "Will there be other activities besides hacking?",
      answer:
        "Of course! We'll have workshops and other activities throughout the event."
    },
    {
      question: "Can I submit my older projects?",
      answer: "You are free to work on any project you like, however we require that all devpost submissions be projects that were made during the hackathon and uniquely for the hackathon."
    },
  ];
  const questionSetRight = [
    {
      question: "What does a virtual hackathon mean?",
      answer:
        "An entirely remote hackathon encompasses everything that an in-person hackathon has, except now you can do it from the comfort of your own bedroom! This includes a Discord server to meet other hackers, pre-recorded workshops, virtual game nights, and a live stream of the closing ceremony."
    },
    {
      question: "Who can apply?",
      answer:
        "Anyone who is 18 years or older (we will be checking ID) and is currently enrolled in college or university with a valid student ID. This means both international and non-Vandy students are welcome, as well!"
    },
    {
      question: "I have no coding experience. Can I still attend?",
      answer:
        "Even more reason for you to come! We will be hosting beginners' workshops for you to get started, and our mentors can help you out along the way. We greatly encourage new hackers to attend, and no prior experience is necessary!"
    },
    {
      question: "How do I submit a project?",
      answer: "This year, we'll be submitting projects on Devpost."
    },
    {
      question: "What if I’m interested in being a mentor?",
      answer: "Send us an email at: info@vandyhacks.org"
    },
    {
      question: "I have more questions!",
      answer:
        "Send us an email at info@vandyhacks.org! We'll be happy to answer!"
    },
  ];
</script>

<style>

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

  h1 {
    color: #ffdb73;
    padding-bottom: 0px;
    margin-bottom: 1%;
    font-family: "Varela Round", sans-serif;
  }

  h2 {
    color: #555560;
    font-size: 3rem;
    font-weight: bold;
    margin: 0px;
    padding: 0px;
  }

  h3 {
    color: #555560;
    font-size: 3rem;
    font-weight: bold;
    margin: 9rem 0 0 0;
    padding: 0px;
    text-align: center;
  }

  .logo {
    color: white;
    padding: 5rem 0 2rem 0;
  }

  .top {
    padding-bottom: 5rem;
  }

  .intro {
    color: #bbbbc4;
    font-size: 1.8rem;
    line-height: 180%;
  }

  .pulled {
    margin-bottom: 9rem;
  }

  .pulled h1 {
    color: white;
    font-size: 3rem;
  }

  .footer {
    padding-top: 5rem;
  }

  .footer p {
    color: white;
    font-size: 1.2rem;
  }

  .visit {
    color: white;
    font-size: 2.2rem;
    background: #32333a;
    width: 18rem;
    padding: 6px;
    border-radius: 10px;
    position: fixed;
    top: 12px;
    right: 20rem;
    text-align: center;
    z-index: 2;
  }

  .header-space {
    height: 4rem;
  }

  /* Mobile first queries */

  /* Larger than mobile */
  @media (min-width: 400px) {
  }

  /* Larger than phablet */
  @media (min-width: 550px) {
  }

  @media (max-width: 550px) {
    .header-space {
      height: 0rem;
    } 
    .leftQuestionSet {
      margin-bottom: 0rem;
    }
    .visit {
      width: 15rem;
      right: 15rem;
      font-size: 1.5rem
    }
    .countdownTitle {
      text-align: left;
    }
  }

  /* Larger than tablet */
  @media (min-width: 750px) {
  }

  /* Larger than desktop */
  @media (min-width: 1000px) {
  }

  /* Larger than Desktop HD */
  @media (min-width: 1200px) {
    h1 {
      font-size: 4rem;
    }
  }
</style>

<a id="mlh-trust-badge" style="display:block;max-width:100px;min-width:60px;position:fixed;right:50px;top:0;width:10%;z-index:10000" href="https://static.mlh.io/docs/mlh-code-of-conduct.pdf" target="_blank"><img src="https://s3.amazonaws.com/logged-assets/trust-badge/2021/mlh-trust-badge-2021-white.svg" alt="Major League Hacking 2021 Hackathon Season" style="width:100%"></a>
<a id="mlh-trust-badge" style="display:block;max-width:100px;min-width:60px;position:fixed;right:50px;top:0;width:10%;z-index:10000" href="https://static.mlh.io/docs/mlh-code-of-conduct.pdf" target="_blank"><img src="https://s3.amazonaws.com/logged-assets/trust-badge/2021/mlh-trust-badge-2021-yellow.svg" alt="Major League Hacking 2021 Hackathon Season" style="width:100%"></a>
<div class="visit" transition:fade={{ duration: 2000 }}>
  <a href="https://apply.vandyhacks.org/" target="_blank">Register here!!!</a>
</div>
<div id="particles-js">
  <div class="container">
    <div class="row top" style="margin-bottom: 3rem">
      <div class="twelve column">
        <div class="logo">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            id="Layer_1"
            data-name="Layer 1"
            viewBox="0 0 430 430" width="9rem" height="9rem">
            <g>
              <path
                style="stroke:#fff; fill:#282931; stroke-width:0.1rem;"
                in:draw={{ duration: 3000 }}
                d="M1259.83 782.15h-18.44a7.3 7.3 0 00-6.38 4.44l-77.7
                209.65-78-209.64a7.32 7.32 0 00-6.39-4.44h-18.44a3.07 3.07 0
                00-3.09 4.44l91.19 245.18a6 6 0 00.93 1.6l-9.83
                26.53-101.27-273.3a7.3 7.3 0 00-6.38-4.44h-18.44a3.08 3.08 0
                00-3.09 4.44l114.16 308a6.59 6.59 0 001.92 2.63 3.1 3.1 0 003.24
                2.13h18.44a6.13 6.13 0 002.11-.41 3.18 3.18 0 001.64-.85 6.91
                6.91 0 002.63-3.19l114.28-308.32a3.08 3.08 0
                00-3.09-4.45zM1354.93 782.15h-18.44a7.3 7.3 0 00-6.38
                4.44L1215.83 1095a3.08 3.08 0 003.09 4.44h18.44a7.31 7.31 0
                006.38-4.44L1358 786.6a3.08 3.08 0 00-3.07-4.45zM1240.89
                960.6h-18.44a7.3 7.3 0 00-6.38 4.44L1167.92 1095a3.07 3.07 0
                003.06 4.44h18.51a7.31 7.31 0 006.3-4.33L1244 965a3.07 3.07 0
                00-3.11-4.4zM1229.63 940.83h18.44a7.3 7.3 0 006.38-4.44L1310
                786.48c.77-2.07-.11-3.8-2-4.29a3.89 3.89 0 00-.42 0H1288a5.22
                5.22 0 00-1.5.25 7.78 7.78 0 00-3.3 2.28 5.24 5.24 0 00-.78
                1.37l-56.1 151.37c-.25 1.91 1.07 3.37 3.31 3.37z"
                class="cls-1"
                transform="translate(-1004.22 -782.15)" />
            </g>
            <g>
              <path
                style="fill:#fff"
                in:expand={{ duration: 4000, delay: 1000 }}
                d="M1259.83 782.15h-18.44a7.3 7.3 0 00-6.38 4.44l-77.7
                209.65-78-209.64a7.32 7.32 0 00-6.39-4.44h-18.44a3.07 3.07 0
                00-3.09 4.44l91.19 245.18a6 6 0 00.93 1.6l-9.83
                26.53-101.27-273.3a7.3 7.3 0 00-6.38-4.44h-18.44a3.08 3.08 0
                00-3.09 4.44l114.16 308a6.59 6.59 0 001.92 2.63 3.1 3.1 0 003.24
                2.13h18.44a6.13 6.13 0 002.11-.41 3.18 3.18 0 001.64-.85 6.91
                6.91 0 002.63-3.19l114.28-308.32a3.08 3.08 0
                00-3.09-4.45zM1354.93 782.15h-18.44a7.3 7.3 0 00-6.38
                4.44L1215.83 1095a3.08 3.08 0 003.09 4.44h18.44a7.31 7.31 0
                006.38-4.44L1358 786.6a3.08 3.08 0 00-3.07-4.45zM1240.89
                960.6h-18.44a7.3 7.3 0 00-6.38 4.44L1167.92 1095a3.07 3.07 0
                003.06 4.44h18.51a7.31 7.31 0 006.3-4.33L1244 965a3.07 3.07 0
                00-3.11-4.4zM1229.63 940.83h18.44a7.3 7.3 0 006.38-4.44L1310
                786.48c.77-2.07-.11-3.8-2-4.29a3.89 3.89 0 00-.42 0H1288a5.22
                5.22 0 00-1.5.25 7.78 7.78 0 00-3.3 2.28 5.24 5.24 0 00-.78
                1.37l-56.1 151.37c-.25 1.91 1.07 3.37 3.31 3.37z"
                class="cls-1"
                transform="translate(-1004.22 -782.15)" />
            </g>
          </svg>
        </div>
        <h1 transition:typewriter={{ delay: 800 }}>VandyHacks - Summer Edition</h1>
        <h2 transition:typewriter={{ delay: 2400 }}>Happening now</h2>
      </div>
    </div>

    <div class="row">
      <div class="two-thirds column pulled" style="margin-bottom: 4.5rem" transition:fly={{ x: -200, duration: 2000, delay: 2500 }}>
        <h1>Links</h1>
        <Links />
      </div>
      
      <!-- countdown -->
      <div class="one-third column pulled"  transition:fly={{ x: 200, duration: 2000, delay: 3000 }}>
      <!-- <div class="pulled"> -->
        <h3 style="margin-top: 0rem" class="countdownTitle">Countdown:</h3>
        <Countdown />
      </div>
    </div>
    

    <div class="row">
      <div class="pulled" transition:fly={{ x: 200, duration: 2000, delay: 3000 }}>
        <h1>Schedule</h1>
        <Schedule />
      </div>
    </div>


    <div class="row">
      <div class="" transition:fly={{ x: -200, duration: 2000, delay: 3000 }}>
        <div class="pulled intro">
          <h1>Welcome!</h1>
          <p>{introText}</p>
        </div>
      </div>
    </div>


    <div class="row">
      <div
        class="one-half column"
        transition:fly={{ x: -200, duration: 2000, delay: 3500 }}>
        <div class="pulled leftQuestionSet" >
          <h1>FAQ</h1>
          <FAQ questionSet={questionSetLeft} identifier="left" />
        </div>
      </div>

      <div
        class="one-half column"
        transition:fly={{ x: 200, duration: 2000, delay: 3500 }}>
        <div class="pulled">
          <div class="header-space" />
          <FAQ questionSet={questionSetRight} identifier="right" />
        </div>
      </div>
    </div>



    <div class="row">
      <div class="pulled" transition:fly={{ y: 200, duratzion: 2000, delay: 3000 }}>
        <h1>Non-profit projects</h1>
        <p class="intro">
          {nonProfitIntro}
          <a target="_blank" href="https://docs.google.com/document/d/13WCPxi8P0_-wx7Cuo60SUuLI1GTgyR2rY379GzL583A/" rel="noreferrer" style="color:#ffdb73">guidelines</a>.
          <b>{nonProfitIntroBold}</b>
          {nonProfitIntroCont}
        </p> 
        <Cards />
      </div>
    </div>



  </div>

  <div class="container">
    <div
      class="footer"
      transition:fly={{ y: 200, duration: 2000, delay: 3500 }}>
      <p>
        Made with ♡ using the awesome
        <a
          target="_blank"
          href="https://github.com/VincentGarreau/particles.js/"
          rel="noreferrer">
          Particles.js
        </a>
        &
        <a target="_blank" href="https://getskeleton.com/" rel="noreferrer">
          Skeleton.css
        </a>
        by
        <a target="_blank" href="https://vandyhacks.org/" rel="noreferrer">
          VandyHacks
        </a>
        (๑¯◡¯๑)
      </p>
    </div>
  </div>

</div>
