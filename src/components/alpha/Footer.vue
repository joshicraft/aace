<template>
  <v-footer>
    <custom-background-vector fill="#212121" position="full-bot" :top="false"></custom-background-vector>
    <v-container fluid class="alpha-footer">
      <v-layout
        row
        wrap
        justify-space-between
        class="grey darken-4 fill-height"
      >
        <v-flex
          xs12
          sm3
          class="pa-5 grey darken-4"
        >
          <h5 class="title pb-3" v-text="company" />
          <ul>
            <li v-for="(item, i) in computedSocial" :key="i">
              <a :href="item.href" class="layout align-center">
                <v-icon
                  dark
                  class="mr-3"
                  v-text="item.icon"
                />
                <span class="subheading" v-text="item.text" />
              </a>
            </li>
          </ul>
        </v-flex>

        <v-flex
                xs12
                sm4
                class="pa-5 grey darken-4"
        >
          <h5 class="title pb-3">
            Contact
          </h5>
          <ul>
            <li>
              <v-layout justify-start row>
                <v-icon
                        dark
                        class="mr-3"
                >
                  phone
                </v-icon>
                <a class="p-format" :href="'tel:' + contact.phone" v-text="contact.phone">
                </a>
              </v-layout>
            </li>
            <li>
              <v-layout justify-start row>
                <v-icon
                        dark
                        class="mr-3"
                >
                  email
                </v-icon>
                <a
                          class="p-format"
                          :href="'mailto:' + contact.email"
                          v-text="contact.email">
                  </a>
              </v-layout>
            </li>
            <li>
              <v-layout justify-start row>
                <v-icon
                        dark
                        class="mr-3"
                >
                  home
                </v-icon>
                <p class="p-format" v-text="contact.address">
                </p>
              </v-layout>
            </li>
            <li>
              <v-layout justify-start row>
                <v-icon
                        dark
                        class="mr-3"
                >
                  access_time
                </v-icon>
                <v-layout justify-start column>
                  <p class="p-format" v-text="contact.hours.weekday">
                  </p>
                  <p class="p-format" v-text="contact.hours.weekend">
                  </p>
                </v-layout>
              </v-layout>
            </li>
          </ul>
        </v-flex>
        <v-flex xs12>
          <v-card
            tile
            flat
            dark
            class="grey darken-3 text-xs-center"
          >
            <v-card-text>
              <slot />
            </v-card-text>
          </v-card>
        </v-flex>
      </v-layout>
    </v-container>
  </v-footer>
</template>

<script>
  export default {
    name: 'alpha-footer',
    props: {
      categories: {
        type: Array,
        default: () => ([])
      },
      company: String,
      facebook: String,
      github: String,
      social: {
        type: Array,
        default: () => []
      },
      twitter: String
    },
    computed: {
      contact () {
        return this.bakedViews.Contact
      },
      computedSocial () {
        if (this.social.length) return this.social

        const social = []

        if (this.github) {
          social.push({
            text: this.$t('Layout.Footer.github'),
            icon: 'mdi-github-circle',
            href: this.github
          })
        }

        if (this.twitter) {
          social.push({
            text: this.$t('Layout.Footer.twitter'),
            icon: 'mdi-twitter-circle',
            href: this.twitter
          })
        }

        if (this.facebook) {
          social.push({
            text: this.$t('Layout.Footer.facebook'),
            icon: 'mdi-facebook-box',
            href: this.facebook
          })
        }

        return social
      }
    }
  }
</script>

<style lang="stylus">

  .v-footer
    position: relative;

  .p-format
      margin-bottom: 0

  .alpha-footer
    background: #cacaca
    color: #fff
    display: block
    padding: 0 !important
    height: auto

    .container
      padding: 0
      margin: 0

    ul
      list-style-type: none
      margin: 0
      padding: 0

      li
        max-height: 1.6em;
        margin-bottom: 10px

      a
        color: #fff
        text-decoration: none
        transition: .2s ease-in

        &:hover
          opacity: .5
</style>
