<template lang="pug">
  v-navigation-drawer(
    v-model="isActive"
    persistent
    :mini-variant.sync="mini"
    dark
    enable-resize-watcher
  )
    v-list.pa-0.vuetify
      v-list-item
        v-list-tile(avatar tag="div")
          v-list-tile-avatar
            router-link(to="/")
              img(src="/static/v.png" v-bind:style="filter")
          v-list-tile-content.show-overflow
            v-menu(transition="v-scale-transition" origin="top")
              v-list-tile-title(slot="activator")
                span Vuetify
                v-icon(light) arrow_drop_down
              v-list(class="grey darken-2")
                v-list-item
                  v-list-tile(href="https://github.com/vuetifyjs/vuetify" target="_blank")
                    v-list-tile-action
                      v-icon(fa light) github
                    v-list-tile-title Github
                v-list-item
                  v-list-tile(href="https://gitter.im/vuetifyjs/Lobby/~chat#" target="_blank")
                    v-list-tile-action
                      v-icon(fa light) comments-o
                    v-list-tile-title Chat
                v-list-item
                  v-list-tile(href="https://twitter.com/vuetifyjs" target="_blank")
                    v-list-tile-action
                      v-icon(fa light) twitter
                    v-list-tile-title Twitter
                v-list-item
                  v-list-tile(href="https://www.facebook.com/vuetifyjs" target="_blank")
                    v-list-tile-action
                      v-icon(fa light) facebook
                    v-list-tile-title Facebook
          v-list-tile-action
            v-btn(icon light v-on:click.native.stop="mini = !mini")
              v-icon chevron_left
    v-divider
    v-list
      template(v-for="item in items")
        v-list-group(v-if="item.items" v-bind:group="item.group")
          v-list-tile(slot="item" ripple)
            v-list-tile-action
              v-icon(light) {{ item.action }}
            v-list-tile-content
              v-list-tile-title {{ item.title }}
            v-list-tile-action
              v-icon(light) keyboard_arrow_down
          v-list-item(v-for="subItem in item.items" v-bind:key="subItem")
            v-list-tile(
              :href="subItem.href"
              v-bind:router="!subItem.target"
              ripple
              v-bind:disabled="subItem.disabled"
              v-bind:target="subItem.target"
            )
              v-list-tile-content
                v-list-tile-title {{ subItem.title }}
              v-list-tile-action(v-if="subItem.action")
                v-icon(light class="success--text") {{ subItem.action }}
        v-subheader(v-else-if="item.header" light) {{ item.header }}
        v-divider(v-else-if="item.divider")
        v-list-item(v-else)
          v-list-tile(:href="item.href" router ripple v-bind:disabled="item.disabled")
            v-list-tile-action
              v-icon(light) {{ item.action }}
            v-list-tile-content
              v-list-tile-title {{ item.title }}
            v-list-tile-action(v-if="item.subAction")
              v-icon(light class="success--text") {{ item.subAction }}
</template>

<script>
  export default {
    data () {
      return {
        mini: false,
        items: [
          { header: 'Core documentation' },
          {
            title: 'Vuetify',
            action: 'apps',
            group: 'vuetify',
            items: [
              { href: '/vuetify/quick-start', title: 'Quick start' }
            ]
          },
          {
            title: 'Motion',
            action: 'slow_motion_video',
            group: 'motion',
            items: [
              { href: '/motion/transitions', title: 'Transitions' }
            ]
          },
          {
            title: 'Style',
            action: 'style',
            group: 'style',
            items: [
              { href: '/style/colors', title: 'Colors' },
              { href: '/style/theme', title: 'Theme' },
              { href: '/style/typography', title: 'Typography' },
              { href: '/style/content', title: 'Content' }
            ]
          },
          {
            title: 'Layout',
            action: 'devices',
            group: 'layout',
            items: [
              { href: '/layout/pre-defined', title: 'Pre-defined' },
              { href: '/layout/grid', title: 'Grid' },
              { href: '/layout/spacing', title: 'Spacing' },
              { href: '/layout/alignment', title: 'Alignment' },
              { href: '/layout/display', title: 'Display' },
              { href: '/layout/elevation', title: 'Elevation' }
            ]
          },
          {
            title: 'Components',
            action: 'widgets',
            group: '/components',
            items: [
              { href: '/components/alerts', title: 'Alerts' },
              { href: '/components/breadcrumbs', title: 'Breadcrumbs' },
              { href: '/components/bottom-navigation', title: 'Bottom navigation' },
              { href: '/components/buttons', title: 'Buttons' },
              { href: '/components/cards', title: 'Cards' },
              { href: '/components/carousels', title: 'Carousel' },
              { href: '/components/chips', title: 'Chips' },
              { href: '/components/data-tables', title: 'Data tables' },
              { href: '/components/dialogs', title: 'Dialogs' },
              { href: '/components/dividers', title: 'Dividers' },
              { href: '/components/expansion-panels', title: 'Expansion panels' },
              { href: '/components/footer', title: 'Footer' },
              { href: '/components/icons', title: 'Icons' },
              { href: '/components/lists', title: 'Lists' },
              { href: '/components/menus', title: 'Menus' },
              { href: '/components/navigation-drawers', title: 'Navigation drawers' },
              { href: '/components/pagination', title: 'Pagination' },
              { href: '/components/parallax', title: 'Parallax' },
              { href: '/components/pickers', title: 'Pickers' },
              { href: '/components/progress', title: 'Progress & activity' },
              { href: '/components/selects', title: 'Selects' },
              { href: '/components/selection-controls', title: 'Selection controls' },
              { href: '/components/sliders', title: 'Sliders' },
              { href: '/components/snackbars', title: 'Snackbars & toasts' },
              { href: '/components/steppers', title: 'Steppers' },
              { href: '/components/subheaders', title: 'Subheaders' },
              { href: '/components/tabs', title: 'Tabs' },
              { href: '/components/text-fields', title: 'Text fields' },
              { href: '/components/toolbars', title: 'Toolbars' }
            ]
          },
          {
            title: 'Directives',
            action: 'polymer',
            group: '/directives',
            items: [
              { href: '/directives/badges', title: 'Badges' },
              { href: '/directives/ripples', title: 'Ripples' },
              { href: '/directives/tooltips', title: 'Tooltips' }
            ]
          },
          { divider: true },
          { header: 'Additional resources' },
          {
            title: 'Ecosystem',
            action: 'public',
            items: [
              {
                href: 'https://vuejobs.com/?ref=vuetify',
                target: '_blank',
                title: 'Jobs',
                action: 'whatshot'
              },
              {
                href: 'https://gitter.im/vuetifyjs/Lobby/~chat#',
                target: '_blank',
                title: 'Chat'
              }
            ]
          },
          {
            title: 'Guides',
            action: 'developer_mode',
            group: '/guides',
            items: [
              {
                href: '/guides/server-side-rendering',
                title: 'Server Side Rendering'
              }
            ]
          },
          {
            title: 'Examples',
            action: 'web',
            items: [
              {
                href: 'https://github.com/nuxt/nuxt.js/tree/master/examples/with-vuetify',
                target: '_blank',
                title: 'NUXT'
              }
            ]
          },
          // { title: 'Optimization', action: 'flash_on', disabled: true },
          // { title: 'Deployment', action: 'important_devices', disabled: true }
        ]
      }
    },

    computed: {
      filter () {
        const color = this.$store.state.currentColor
        let hue = 0

        if (color === 'purple') {
          hue = 420
        } else if (color === 'darken-3 pink') {
          hue = 480
        } else if (color === 'indigo') {
          hue = 370
        } else if (color === 'cyan') {
          hue = 337
        } else if (color === 'teal') {
          hue = 315
        }

        return {
          filter: `hue-rotate(${hue}deg)`
        }
      },

      isActive: {
        get () {
          return this.$store.state.sidebar
        },
        set (val) {
          this.$store.commit('vuetify/SIDEBAR', val)
        }
      }
    }
  }
</script>

<style lang="stylus">
  .vuetify
    .router-link-active
      display: flex
      align-items: center

    .list__tile__avatar img
      border-radius: 0 !important
</style>
