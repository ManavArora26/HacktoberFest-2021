<template>
  <Container name="contributor">
    <section class="content-section">
      <HashHeader title="CONTRIBUTORS" />
      <div class="contents">
        <div class="contributors-grid">
          <div
            v-for="(contributor, index) in contributors"
            :key="index"
            :class="[
              'contributor-card',
              `rot-${Math.floor(Math.random() * 24) * 15}`
            ]"
          >
            <a
              :href="contributor.url"
              target="_blank"
              rel="noopener noreferrer"
            >
              <div class="picture-wrapper smooth-transition">
                <img
                  :src="contributor.picture"
                  alt="profile picture"
                  class="profile-pic"
                />
              </div>
            </a>
            <h4 class="title">{{ contributor.name }}</h4>
            <p v-if="contributor.description" class="description">
              {{ contributor.description }}
            </p>
          </div>
        </div>
      </div>
    </section>
  </Container>
</template>

<script>
import Container from "~/components/Container";
import HashHeader from "~/components/HashHeader";

export default {
  components: {
    Container,
    HashHeader
  },
  data() {
    return {
      contributors: [
        {
          name: "Apoorv Dwivedi",
          url: "https://www.linkedin.com/in/apoorvdwi",
          picture: require("~/assets/Contributors/apoorv.jpeg"),
          description:
            "SWE Intern at Intervue | Microsoft Learn Student Ambassador | Core Team - HackOn 2.0, HackThisFall 2.0"
        },
        // Add you data here in the above format, don't change the existing order
      ]
    };
  }
};
</script>

<style lang="scss" scoped>
.content-section {
  display: flex;
  flex-direction: column;
  padding: 20px 0;
  font-family: "Segoe UI";
  margin: 2rem 0 1rem 0;

  .contents {
    padding: 1rem 4rem;
    text-align: center;

    @include respond-below(lg) {
      padding: 1rem 0rem;
    }

    .contributors-grid {
      display: grid;
      grid-template-columns: repeat(4, 1fr);
      column-gap: 20px;
      row-gap: 20px;

      @include respond-below(md) {
        grid-template-columns: repeat(3, 1fr);
      }

      @include respond-below(sm) {
        grid-template-columns: repeat(2, 1fr);
      }

      @include respond-below(xs) {
        grid-template-columns: repeat(1, 1fr);
      }

      .contributor-card {
        padding: 0.5rem 0 1rem;
        display: flex;
        flex-direction: column;
        box-shadow: rgba(255, 107, 0, 0.07) 0px 0px 10px 2px;
        border-radius: 1rem;
        // justify-content: center;
        align-items: center;

        .picture-wrapper {
          border-style: solid;
          border-width: 3px;
          border-color: red red white red;
          width: 210px;
          height: 210px;
          display: flex;
          align-items: center;
          justify-content: center;
          border-radius: 50%;
          margin-top: 1rem;

          .profile-pic {
            width: 200px;
            height: 200px;
            border-radius: 50%;
            // background: var(red);
          }

          @include respond-below(md) {
            width: 170px;
            height: 170px;
            .profile-pic {
              width: 160px;
              height: 160px;
            }
          }

          @include respond-below(sm) {
            width: 140px;
            height: 140px;
            .profile-pic {
              width: 130px;
              height: 130px;
            }
          }
        }

        .title {
          font-size: 1.2rem;
          text-align: center;
          margin: 1rem 0rem;
          color: rgba(233, 83, 34, 1);

          @include respond-below(sm) {
            font-size: 1rem;
            margin-top: 10px;
          }
        }

        .description {
          margin: 0 0.5rem 0.5rem;
          font-size: 1rem;
          color: #2b3531;
          line-height: 1.3rem;
          opacity: 0.7;
          text-align: center;
        }
      }
    }
  }
}
</style>
