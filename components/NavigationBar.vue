<template>
  <div class="navigation-bar">
    <div class="no-extend">
      <div class="navigation-contents">
        <!-- Branding area -->
        <div class="branding">
          <NuxtLink to="/">
            <img class="headerImage" src="~/assets/hacktoberfestLogo.svg" />
          </NuxtLink>
        </div>
        <!-- Menu area -->
        <div class="menu-area">
          <ul class="nav-links">
            <li
              v-for="(navlink, index) in navlinks"
              :key="index"
              :id="'nav-link-' + navlink.text"
            >
              <a target="_blank" :href="navlink.link">{{ navlink.text }}</a>
            </li>
          </ul>
        </div>
      </div>
    </div>
    <Slide class="slidingDrawer" :closeOnNavigation="true">
      <a target="_blank" v-for="(navlink, index) in navlinks" :key="index" :href="navlink.link">
        <span>{{ navlink.text }}</span>
      </a>
    </Slide>
  </div>
</template>

<script>
import { Slide } from "vue-burger-menu";

export default {
  data() {
    return {
      navlinks: [
        {
          link: "https://hacktoberfest.digitalocean.com/",
          text: "Official Website"
        },
        {
          link: "https://hacktoberfest.digitalocean.com/resources",
          text: "Resources"
        },
        {
          link: "https://hacktoberfest.digitalocean.com/events",
          text: "Events"
        },
        {
          link: "https://github.com/apoorvdwi/HacktoberFest-2021",
          text: "Github"
        }
      ]
    };
  },
  components: {
    Slide
  }
};
</script>

<style lang="scss">
.navigation-bar {
  background-color: rgba(255, 255, 255, 0.8);
  box-shadow: rgba(157, 157, 157, 0.26) 0px 0px 40px;
  z-index: 500;
  padding: 0rem 1.5rem;
  position: fixed;
  width: 100%;
  border-radius: 1rem;
  margin: 0 auto -3rem auto;
  height: auto;
  backdrop-filter: blur(30px);

  @include respond-below(md) {
    margin: unset;
    width: 60px;
    height: 45px;
    top: 1rem;
    padding: 0px 15px;
    left: 1rem;
  }

  .slidingDrawer {
    min-height: 100vh !important;
    @include respond-above(md) {
      display: none;
    }
    a {
      span {
        text-transform: uppercase;
      }
    }
  }

  .navigation-contents {
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    margin: 0.25rem 0rem;
    padding-right: 3rem;

    @include respond-below(md) {
      display: none;
    }

    @include respond-below(sm) {
      justify-content: center;
    }

    .branding {
      .headerImage {
        height: 2.5rem;
        margin-bottom: -0.1rem;
      }
    }

    .menu-area {
      display: flex;
      align-items: center;

      @include respond-below(md) {
        display: none;
      }

      @include respond-below(sm) {
        display: none;
      }

      ul.nav-links {
        display: flex;
        align-items: center;
        font-weight: 600;

        li {
          margin-right: 1.7rem;
          @media (max-width: 850px) {
            margin-right: 0.5rem;
          }
          @media (max-width: 790px) {
            margin-right: 0.3rem;
          }
          &:nth-last-of-type(1) {
            margin-right: 0;
          }
          list-style: none;

          a {
            color: #848484;
            padding: 10px 10px;
            transition: 0.2s all ease-in-out;
            text-decoration: none;
            font-size: 1.1rem;
            opacity: 0.95;
            text-transform: uppercase;

            &:hover {
              color: rgba(226, 62, 37, 1);
              opacity: 1;
            }

            .btn {
              font-family: "Open Sans";
              background-color: #3067f0;
              border: none;
              color: white;
              font-weight: 700;
              font-size: 1.1rem;
              border-radius: 0.2rem;
              padding: 0.75rem 2.5rem;
              cursor: pointer;
              transition: 0.2s;
              opacity: 0.95;

              @media (max-width: 850px) {
                padding: 0.75rem 1rem;
              }

              @media (max-width: 790px) {
                padding: 0.75rem 0.5rem;
              }

              &:hover {
                background-color: #1656f7;
                opacity: 1;
              }
            }
          }
        }
      }
    }
  }
}

.bm-burger-button {
  position: sticky;
  width: 30px;
  height: 25px;
  left: 36px;
  margin-top: 0.6rem;
  cursor: pointer;
}
.bm-burger-bars {
  background-color: #e85325;

  @include respond-above(lg) {
    display: none;
  }
}
.line-style {
  position: absolute;
  height: 20%;
  left: 0;
  right: 0;
}
.cross-style {
  position: absolute;
  top: 12px;
  right: 2px;
  cursor: pointer;
}
.bm-cross {
  background: #e85325;
}
.bm-cross-button {
  margin-top: 4px;
  height: 24px;
  width: 24px;
}
.bm-menu {
  height: 96vh; /* 100% Full-height */
  border-radius: 1rem;
  width: 0; /* 0 width - change this with JavaScript */
  position: fixed; /* Stay in place */
  z-index: 1000; /* Stay on top */
  top: 0;
  left: 0;
  background-color: #feede3; /* Black*/
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 60px; /* Place content 60px from the top */
  transition: 0.5s; /*0.5 second transition effect to slide in the sidenav*/
}

.bm-overlay {
  background: rgba(0, 0, 0, 0.3);
}
.bm-item-list {
  color: #848484;
  margin-left: 10%;
  font-size: 20px;
}
.bm-item-list > * {
  display: flex;
  text-decoration: none;
  padding: 0.7em;
}
.bm-item-list > * > span {
  margin-left: 10px;
  font-weight: 700;
  color: #848484;

  &:hover {
    color: #e85325;
  }
}
</style>
