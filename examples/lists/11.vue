<template>
  <v-layout row>
    <v-flex xs12 sm6 offset-sm3>
      <v-card>
        <v-toolbar class="teal white--text">
          <v-toolbar-side-icon light></v-toolbar-side-icon>
          <v-toolbar-title>Kitchen Sink Mash-Up</v-toolbar-title>
          <v-btn light icon>
            <v-icon>more_vert</v-icon>
          </v-btn>
        </v-toolbar>

        <v-list subheader>
          <v-subheader>Normal "un-dense" Chat</v-subheader>
          <v-list-item v-for="item in contacts" v-bind:key="item.title">
            <v-list-tile avatar>
              <v-list-tile-avatar>
                <img v-bind:src="item.avatar"/>
              </v-list-tile-avatar>
              <v-list-tile-content>
                {{item.title}}
              </v-list-tile-content>
              <v-list-tile-action>
                <v-btn v-if="item.active" dark ripple small style="min-width:40px">
                  Foo
                </v-btn>
                <v-icon v-else v-bind:class="[item.active ? 'teal--text' : 'grey--text']">
                  chat_bubble
                </v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list-item>

          <v-list-item>
            <v-list-tile avatar>
              <v-list-tile-action>
                <v-btn class="pink--text" icon>
                  <v-icon >star</v-icon>
                </v-btn>
              </v-list-tile-action>
              <v-list-tile-content>
                <v-list-tile-title >Jim</v-list-tile-title>
              </v-list-tile-content>
              <v-list-tile-avatar>
                <img src="/static/doc-images/lists/1.jpg"/>
              </v-list-tile-avatar>
            </v-list-tile>
          </v-list-item>
        </v-list>

        <v-list subheader dense>
          <v-subheader>Recent dense chat</v-subheader>
          <v-list-item v-for="item in contacts" v-bind:key="item.title">
            <v-list-tile avatar>
              <v-list-tile-avatar>
                <img v-bind:src="item.avatar"/>
              </v-list-tile-avatar>
              <v-list-tile-content>
                <v-list-tile-title v-html="item.title"></v-list-tile-title>
              </v-list-tile-content>
              <v-list-tile-action>
                <v-btn v-if="item.active" icon>
                  <v-icon >star</v-icon>
                </v-btn>
                <v-icon v-else dark>chat_bubble</v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list-item>
          <v-list-item>
            <v-list-tile avatar>
              <v-list-tile-action>
                <v-btn class="pink--text" icon>
                  <v-icon >star</v-icon>
                </v-btn>
              </v-list-tile-action>
              <v-list-tile-content>
                <v-list-tile-title >Jim</v-list-tile-title>
              </v-list-tile-content>
              <v-list-tile-action>
                <v-icon >star</v-icon>
              </v-list-tile-action>
            </v-list-tile>
          </v-list-item>
        </v-list>



        <v-list dense>
          <v-subheader>Menu Avatar Dense Expansion</v-subheader>
          <v-divider></v-divider>
          <v-list-group v-for="item in items" :value="item.active" v-bind:key="item.title">

            <v-list-tile avatar slot="item">
              <v-list-tile-avatar>
                <v-icon class='blue white--text'>{{ item.action }}</v-icon>
              </v-list-tile-avatar>
              <v-list-tile-content>
                <v-list-tile-title>{{ item.title }}</v-list-tile-title>
              </v-list-tile-content>
              <v-list-tile-action>
                <v-icon dark>keyboard_arrow_down</v-icon>
              </v-list-tile-action>
            </v-list-tile>

            <v-list-item v-for="subItem in item.items" v-bind:key="subItem.title">

              <v-subheader v-if="subItem.title === 'New American'" :inset="true">Favs</v-subheader>
              <v-divider v-if="subItem.title === 'New American'"  :inset="true"></v-divider>

              <v-list-tile>
                <v-list-tile-content>
                  <v-list-tile-title>{{ subItem.title }}</v-list-tile-title>
                </v-list-tile-content>
                <v-list-tile-action>
                  <v-icon dark>{{ subItem.action }}</v-icon>
                </v-list-tile-action>
              </v-list-tile>

            </v-list-item>
          </v-list-group>
        </v-list>

        <v-list dense two-line>
          <v-subheader>Notifications</v-subheader>

          <v-list-item>
            <v-list-tile>
              <v-list-tile-action>
                <v-checkbox></v-checkbox>
              </v-list-tile-action>
              <v-list-tile-content>
                <v-list-tile-title>Notifications 40px high</v-list-tile-title>
                <v-list-tile-sub-title>will be 13 px across board on dense</v-list-tile-sub-title>
              </v-list-tile-content>
            </v-list-tile>
          </v-list-item>
        </v-list>

        <v-list dense>
          <v-subheader>Menu Dense Expansion - no avatar</v-subheader>
          <v-list-group v-for="item in items" :value="item.active" v-bind:key="item.title">

            <v-list-tile slot="item">
              <v-list-tile-action>
                <v-icon >{{ item.action }}</v-icon>
              </v-list-tile-action>
              <v-list-tile-content>
                <v-list-tile-title>{{ item.title }}</v-list-tile-title>
              </v-list-tile-content>
              <v-list-tile-action>
                <v-icon dark>keyboard_arrow_down</v-icon>
              </v-list-tile-action>
            </v-list-tile>

            <v-list-item v-for="subItem in item.items" v-bind:key="subItem.title">
              <v-list-tile>
                <v-list-tile-content>
                  <v-list-tile-title>{{ subItem.title }}</v-list-tile-title>
                </v-list-tile-content>
                <v-list-tile-action>
                  <v-icon dark>{{ subItem.action }}</v-icon>
                </v-list-tile-action>
              </v-list-tile>

            </v-list-item>
          </v-list-group>
        </v-list>

        <v-list>
          <v-list-group v-for="item in items" :value="item.active" v-bind:key="item.title">
            <v-list-tile slot="item">
              <v-list-tile-action>
                <v-icon dark>{{ item.action }}</v-icon>
              </v-list-tile-action>
              <v-list-tile-content>
                <v-list-tile-title>{{ item.title }}</v-list-tile-title>
              </v-list-tile-content>
              <v-list-tile-action>
                <v-icon dark>keyboard_arrow_down</v-icon>
              </v-list-tile-action>
            </v-list-tile>
            <v-list-item v-for="subItem in item.items" v-bind:key="subItem.title">
              <v-list-tile>
                <v-list-tile-content>
                  <v-list-tile-title>{{ subItem.title }}</v-list-tile-title>
                </v-list-tile-content>
                <v-list-tile-action>
                  <v-icon dark>{{ subItem.action }}</v-icon>
                </v-list-tile-action>
              </v-list-tile>
            </v-list-item>
          </v-list-group>
        </v-list>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    data () {
      return {
        contacts: [
          { active: true, title: 'Jason Oner', avatar: '/static/doc-images/lists/1.jpg' },
          { active: false, title: 'Ranee Carlson', avatar: '/static/doc-images/lists/2.jpg' }
        ],
        items: [
          {
            action: 'restaurant',
            title: 'Dining',
            items: [
              { title: 'Breakfast & brunch' },
              { title: 'New American', action: 'favorite' },
              { title: 'Sushi', action: 'favorite' }
            ]
          },
          {
            action: 'chrome_reader_mode',
            title: 'Education',
            items: [
              { title: 'List Item' }
            ]
          }
        ]
      }
    }
  }
</script>

<style lang="stylus">
//fix toolbar
.toolbar > *:first-child
  margin-left: 8px

.toolbar > *:last-child
    margin-right: 4px;
</style>
