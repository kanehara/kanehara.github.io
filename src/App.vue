<template>
  <div id="app">
    <div id="content">
      <transition name="slide-fade">
        <div id="bio" v-if="displayBio">
          <div>
            <img id="avatar" 
                  src="assets/avatar.png" 
                  :class="{animating: isAvatarAnimating}"
                  @mouseenter="animateAvatar"
                  @mouseleave="animateAvatar"/>
          </div>
          <div>
            <h1>Yohei Kanehara</h1>
            <h2>Software Engineer</h2>
          </div>
        </div>
      </transition>
      <transition name="slide-fade">
        <div id="contact" v-if="displayBio">
          <a href="https://github.com/kanehara" target="_blank">
            <img width="50px" src="assets/github.png"/>
          </a>
          <a href="https://www.linkedin.com/in/yohei-kanehara-5b492670" target="_blank">
            <img width="50px" src="assets/linkedin.png"/>
          </a>
        </div>
      </transition>
      <transition name="slide-fade">
        <div id="portfolio" v-if="displayPortfolio">
          <h1>Projects</h1>
          <Portfolio :projects="projects"/>
        </div>
      </transition>
    </div>
    <Space/>
  </div>
</template>

<script>
import Space from './Space'
import Portfolio from './Portfolio'

export default {
  name: 'app',
  components: {
    Space,
    Portfolio
  },
  data() {
    return {
      displayBio: false,
      displayPortfolio: false,
      isAvatarAnimating: false,
      projects: [
        {
          name: "Spotimix",
          href: "http://www.spotimix.com",
          backgroundImage: "assets/Spotimix.png",
          description: "A GraphQL webapp to query Spotify's recommendation API"
        }
      ]
    }
  },
  mounted() {
    this.displayBio = true
    this.displayPortfolio = true
  },
  methods: {
    animateAvatar() {
      this.isAvatarAnimating = !this.isAvatarAnimating;
    }
  }
}
</script>

<style lang="scss">
.slide-fade-enter-active {
  transition: all .8s cubic-bezier(.76,-0.1,.7,.21);
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to {
  transform: translateX(10px);
  opacity: 0;
}

@import './theme.scss';

#content {
  position: absolute;
  margin: 25px 0;
  width: 100%;
  color: $primaryColor;
  font-family: monospace;
}

#bio {
  text-shadow: .5px .5px $secondaryColor;
  font-size: .6rem;
  display: flex;
}

#avatar {
  height: 120px;
  position: relative;

  &:hover {
    cursor: pointer;
  }
  
  $bounce-ammount: 3;
  @keyframes bounce {
    0% {
      top: 0px;
    }
    5% {
      top: -1*($bounce-ammount/5)+px;
    }
    10% {
      top: -2*($bounce-ammount/5)+px;
    }
    15% {
      top: -3*($bounce-ammount/5)+px;
    }
    20% {
      top: -4*($bounce-ammount/5)+px;
    }
    25% {
      top: -5*($bounce-ammount/5)+px;
    }
    30% {
      top: -4*($bounce-ammount/5)+px;
    }
    35% {
      top: -3*($bounce-ammount/5)+px;
    }
    40% {
      top: -2*($bounce-ammount/5)+px;
    }
    45% {
      top: -1*($bounce-ammount/5)+px;
    }
    50% {
      top: 0px;
    }
    55% {
      top: 1*($bounce-ammount/5)+px;
    }
    60% {
      top: 2*($bounce-ammount/5)+px;
    }
    65% {
      top: 3*($bounce-ammount/5)+px;
    }
    70% {
      top: 4*($bounce-ammount/5)+px;
    }
    75% {
      top: 5*($bounce-ammount/5)+px;
    }
    80% {
      top: 4*($bounce-ammount/5)+px;
    }
    85% {
      top: 3*($bounce-ammount/5)+px;
    }
    90% {
      top: 2*($bounce-ammount/5)+px;
    }
    95% {
      top: 1*($bounce-ammount/5)+px;
    }
    100% {
      top: 0px;
    }
  }
  &.animating {
    animation-name: bounce;
    animation-duration: 1s;
    animation-iteration-count: infinite;
    animation-timing-function: ease-in-out;
  }
}

#contact {
  position: absolute;
  right: 25px;
  top: 0;
  font-size: 1.5rem;

  a {
    color: $primaryColor;
    text-decoration: none; 
    text-shadow: .5px .5px $secondaryColor;
  }
  .github.icon {
    &:hover {
      color: $secondaryColor;
    }
  }

  .linkedin.icon {
    &:hover {
      color: $secondaryColor;
    }
  }
}

#portfolio {
  display: flex;
  align-items: center;
  flex-direction: column;
}

body {
  margin: 0;
  font-size: 14px;
}

a:-webkit-any-link {
  text-decoration: none;
  color: inherit;
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}
</style>
