<template>
    <div class="pageBody customStyles pixelated">
        <!-- TODO: add NavBanner later <NavBanner useCustomStyles="true" /> -->
        <div class="pageFrame">
        <slot v-if="noPageContent"></slot>
        <div v-else class="pageContent">
            <slot></slot>
        </div>
        </div>
        <!-- <PageFooter /> -->
    </div>
</template>
  
<script setup>
    // this file is currently unused, I wrongly thought it was used in MspaPage
    // import NavBanner from './NavBanner.vue'
    // import PageFooter from './PageFooter.vue'

    defineProps({
    noPageContent: Boolean
    })
</script>

  
<style scoped lang="scss">
  .pageBody {
    color: var(--font-default);
    background: var(--page-pageBody);

    margin: 0;
    padding: 0;
    display: flex;
    flex-flow: column;
    flex: 1 0 auto;
    align-items: center;

    > img {
      align-self: center;
    }
    ::v-deep a {
      color: var(--page-links);
    }

    //Small screen check
    @media only screen and (max-width: 850px) {
      &{
        overflow-x: hidden;
        height: max-content;
        .navBanner {
          max-width: 100%;
        }
        .pageFrame {
          max-width: 100%;
        }
        ::v-deep div.footer {
          max-width: 100%;
        }
      }
    }

    .pageFrame {
      background: var(--page-pageFrame);

      width: 950px;
      padding-top: 7px;
      padding-bottom: 23px;
      margin: 0 auto;

      // Elements position top-to-bottom, centered.
      flex: 0 1 auto;
      display: flex;
      align-items: center;
      flex-direction: column;

      .pageContent {
        background: var(--page-pageContent);
        max-width: 950px;
        min-width: 650px;

        // Elements position top-to-bottom, centered.
        display: flex;
        flex: 0 1 auto;
        align-items: center;
        flex-flow: column;

        h2.pageTitle {
          max-width: 100%;
          text-align: center;
          line-height: 1.1;
          font-size: 32px;
          padding: 15px 0;
        }

        .logo {
          margin-bottom: 25px;
        }

        .mediaContent {
          display: flex;
          align-items: center;
          flex-flow: column;
          .panel {
            &:not(:last-child) {
              margin-bottom: 20px;
            }
          }
        }

        .textContent {
          margin-top: 15px;
          margin-bottom: 30px;
          display: flex;
          flex-direction: column;
          align-items: center;
          p {
            margin-top: 15px;
          }
        }

      }	
    }
  }
  // MSPA logo hack (see /unlock/x)
  .retro {
    .pageContent {
      background: #EEEEEE !important;
    }
    .mediaContent, .textContent {
      background: white;
    }
  }
</style>

