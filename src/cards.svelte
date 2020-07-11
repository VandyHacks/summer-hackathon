<script>
// note svg elements from here: https://github.com/Keyamoon/IcoMoon-Free/tree/master/SVG
const fillColor = '#555560';
const card_data = [
  {
    'title': 'The Next Door',
    'link': 'https://thenextdoor.org/',
    'icon': '<path fill="#555560" d="M13.5 0c1.381 0 2.5 1.119 2.5 2.5 0 0.563-0.186 1.082-0.5 1.5l-1 1-3.5-3.5 1-1c0.418-0.314 0.937-0.5 1.5-0.5zM1 11.5l-1 4.5 4.5-1 9.25-9.25-3.5-3.5-9.25 9.25zM11.181 5.681l-7 7-0.862-0.862 7-7 0.862 0.862z"/>',
    'details': "The Next Door offers a safe place for women to receive treatment for drug and alcohol abuse. Their project involves building a new event-tracking software such that they can better track information about their volunteer and sponsor networks.",
  },
  {
    'title': 'Nashville Entrepreneur Center',
    'link': 'https://www.ec.co/',
    'icon': '<path fill="#555560" d="M16 15v-1h-1v-6h1v-1h-3v1h1v6h-3v-6h1v-1h-3v1h1v6h-3v-6h1v-1h-3v1h1v6h-3v-6h1v-1h-3v1h1v6h-1v1h-1v1h17v-1h-1z"/> \
             <path fill="#555560" d="M8 0h1l8 5v1h-17v-1l8-5z"/>',
    'details': 'Nashville Entrepreneur Center works towards building a robust entrepreneurial network in Nashville. The project they need help with is building a centralized database of resources and an automated recommendation system for local start-ups.',
  },
  {
    'title': 'Hands On Nashville',
    'link': 'https://www.hon.org/',
    'icon': '<path fill="#555560" d="M8 0c-4.418 0-8 3.582-8 8s3.582 8 8 8 8-3.582 8-8-3.582-8-8-8zM8 15c-0.984 0-1.92-0.203-2.769-0.57l3.643-4.098c0.081-0.092 0.126-0.21 0.126-0.332v-1.5c0-0.276-0.224-0.5-0.5-0.5-1.765 0-3.628-1.835-3.646-1.854-0.094-0.094-0.221-0.146-0.354-0.146h-2c-0.276 0-0.5 0.224-0.5 0.5v3c0 0.189 0.107 0.363 0.276 0.447l1.724 0.862v2.936c-1.813-1.265-3-3.366-3-5.745 0-1.074 0.242-2.091 0.674-3h1.826c0.133 0 0.26-0.053 0.354-0.146l2-2c0.094-0.094 0.146-0.221 0.146-0.354v-1.21c0.634-0.189 1.305-0.29 2-0.29 1.1 0 2.141 0.254 3.067 0.706-0.065 0.055-0.128 0.112-0.188 0.172-0.567 0.567-0.879 1.32-0.879 2.121s0.312 1.555 0.879 2.121c0.569 0.569 1.332 0.879 2.119 0.879 0.049 0 0.099-0.001 0.149-0.004 0.216 0.809 0.605 2.917-0.131 5.818-0.007 0.027-0.011 0.055-0.013 0.082-1.271 1.298-3.042 2.104-5.002 2.104z"/>',
    'details': 'Hands On Nashville connects volunteers to opportunities supporting 100+ nonprofits, schools, and other civic organizations. They are looking to build a platform to easily communicate with and manage volunteers and track attendance of their events.',
  },
] 

const card_data_2 = [
  {
    'title': 'Sexual Assault Center',
    'link': 'https://www.sacenter.org/',
    'icon': '<path fill="#555560" d="M16 9.226l-8-6.21-8 6.21v-2.532l8-6.21 8 6.21zM14 9v6h-4v-4h-4v4h-4v-6l6-4.5z">',
    'details': 'The Sexual Assault Center is dedicated to providing healing for children, adults, and families affected by sexual assault. They are looking for 1) a dashboard application for entering and compiling data and 2) a mobile app for appointment checkins and paperwork.',
  },
  {
    'title': 'Water Walkers',
    'link': 'https://www.waterwalkerstn.org/',
    'icon': '<path fill="#555560" d="M15.802 2.102c-1.73-1.311-4.393-2.094-7.124-2.094-3.377 0-6.129 1.179-7.549 3.235-0.667 0.965-1.036 2.109-1.097 3.398-0.054 1.148 0.139 2.418 0.573 3.784 1.482-4.444 5.622-7.923 10.395-7.923 0 0-4.466 1.175-7.274 4.816-0.002 0.002-0.039 0.048-0.103 0.136-0.564 0.754-1.055 1.612-1.423 2.583-0.623 1.482-1.2 3.515-1.2 5.965h2c0 0-0.304-1.91 0.224-4.106 0.873 0.118 1.654 0.177 2.357 0.177 1.839 0 3.146-0.398 4.115-1.252 0.868-0.765 1.347-1.794 1.854-2.882 0.774-1.663 1.651-3.547 4.198-5.002 0.146-0.083 0.24-0.234 0.251-0.402s-0.063-0.329-0.197-0.431z"></path>',
    'details': 'Water Walkers aims to bring hope to Nashville’s inner-city through watersports and education. Their project is a web-based solution to tracking attendance and storing and quickly accessing student information.',
  },
    {
    'title': 'Alive Hospice',
    'link': 'https://www.alivehospice.org/',
    'icon': '<path fill="#555560" d="M0 16h8v-16h-8v16zM5 2h2v2h-2v-2zM5 6h2v2h-2v-2zM5 10h2v2h-2v-2zM1 2h2v2h-2v-2zM1 6h2v2h-2v-2zM1 10h2v2h-2v-2zM9 5h7v1h-7zM9 16h2v-4h3v4h2v-9h-7z"/>',
    'details': 'Alive Hospice provides loving care to people with life-threatening illnesses, support to their families, and service to the community in a spirit of enriching lives. Their project is a mobile application, where their clients can share their stories by answering interview questions through video and audio recording.',
  },
]

</script>

<style>
* { box-sizing: border-box; }

.card-grid-view {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  
  margin: 1rem; 
}

.card-body {  
  border-radius: 4px;
  color: #bbbbc4;
  
  margin: 1.5rem;
  cursor: pointer;

  /* margin-left: auto;
  margin-right: auto; */
  margin-top: 4rem;
  /* important variable */
  min-height: 45em;
  background-color: rgba(0, 0, 0, 0.2);

  transition: all 0.2s ease-out;
}
.card-body:hover {
  box-shadow: 0 0 2em 0px rgba(0, 0, 0, 0.4);
  transform: scale(1.01);
  background: #ffdb73;
  color: #32333a;
}
.card-body:click {
  box-shadow: 0 0 2em 0px rgba(0, 0, 0, 0.4);
  transform: scale(1.01);
  background: #ffdb73;
  color: #32333a;
}

.card-body:active {
  transform: scale(1.01) translateY(0.2rem);
}
.card-body > .icon-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.2);
}
.card-body .icon { padding: 5.8rem 0; }

.card-body > .text-wrapper {
  padding: 1.5em;
  padding-bottom: 2.7rem;
  border-radius: 0 0 4px 4px;
}

.text-wrapper > .title {
  font-size: 1.3em;
  font-weight: bold;
  margin-bottom: 1.2em;
}
.text-wrapper > .details {
  font-size: 1.1em;
  line-height: 1.7em;
}

@media (max-width: 550px) {
    .card-body {
      min-height: 0rem;
    } 
  }

a {
  text-decoration: none;
}
</style>

<!-- create a map -->
<!-- note that the cards are designed to be mult of 3 -->
<cards class="card-grid-view">

<row>
{#each card_data as item}
<div class="one-third column" >
  <a target="_blank" href={item.link} rel="noopener noreferrer">
  <div class="card-body">
    <div class="icon-wrapper section">
      <div class="icon">
        <!-- <i class={item.icon} aria-hidden="true"></i> -->
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="6rem" height="6rem" viewBox="0 0 16 16">
          {@html item.icon}
        </svg>
      </div>
    </div>
    <div class="text-wrapper section">
      <div class="title">{ item.title }</div>
      <div class="details">{ item.details }</div>
    </div>
  </div>
  </a>
</div>
{/each}
</row>

<row>
{#each card_data_2 as item}
<div class="one-third column">
  <a target="_blank" href={item.link} rel="noopener noreferrer">
  <div class="card-body">

    <div class="icon-wrapper section">
      <div class="icon">
        <!-- <i class={item.icon} aria-hidden="true"></i> -->
        <svg xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="6rem" height="6rem" viewBox="0 0 16 16">
          {@html item.icon}
        </svg>
      </div>
    </div>
    <div class="text-wrapper section">
      <div class="title">{ item.title }</div>
      <div class="details">{ item.details }</div>
    </div>
  </div>
  </a>
</div>

{/each}
</row>
</cards>

