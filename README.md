# Frontend Mentor - Time tracking dashboard solution

This is a solution to the [Time tracking dashboard challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/time-tracking-dashboard-UIQ7167Jw). Frontend Mentor challenges help you improve your coding skills by building realistic projects. 

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
- [Author](#author)


## Overview

### The challenge

Users should be able to:

- View the optimal layout for the site depending on their device's screen size
- See hover states for all interactive elements on the page
- Switch between viewing Daily, Weekly, and Monthly stats

### Links

- Live Site URL: https://kris-sand0.github.io/time-tracking-dashboard/

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties
- Flexbox
- CSS Grid
- Mobile-first workflow
- Vanilla JavaScript

### What I learned

In this project, I've learned how to:

- Use the `fetch` API to get data from a local JSON file.
- Dynamically generate HTML elements with JavaScript.
- Handle events to switch between different views (daily, weekly, monthly).
- Use CSS Grid and Flexbox to create a responsive layout.
- Use CSS custom properties to manage the color palette.

Here's a code snippet of the JavaScript code that fetches the data and displays it:

```javascript
async function fetchData() {
  const response = await fetch('./data.json')
  statsData = await response.json()
  displayData(selectedTimeframe)
  
}

function displayData(timeframe) {
  dashboardContainer.querySelectorAll('.card').forEach(card => card.remove())

  statsData.forEach(stat => {
    const item = document.createElement('div')
    item.classList.add('card', `${stat.title.toLowerCase().replace(' ', '-')}-card`)

    // get timeframe data

    const timeData = stat.timeframes[timeframe]
    const previousLabel = timeframe === 'daily' ? 'Yesterday' : timeframe === 'weekly' ? 'Last Week' : 'Last Month'

    item.innerHTML = `
      <div class="card-top">
        
      </div>
      <div class="card-bottom">
        <div class='card-header'>
          <p class='title bold-text'>${stat.title}</p>
          <div class='menu-btn'><i class='ri-more-fill'></i></div>
        </div>
        <div class='time'>
          <p class='current-hours big-text'>${timeData.current}hrs</p>
          <p class='previous-hours small-text'>${previousLabel} - <span class="previous-hours">${timeData.previous}</span>hrs</p>
      </div>
    `

    dashboardContainer.appendChild(item)

  })
}
```

## Author

- Frontend Mentor - https://www.frontendmentor.io/profile/kris-sand0
