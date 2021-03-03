<template>
  <div class="dashboard">
    <h2 class="subheading pa-5 grey--text ">Dashboard</h2>
    <v-container class="pa-5">

      <v-layout class="my-3" row wrap>


        <v-flex lg2 md2 sm6>
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-btn icon x-large @click="sortBy('title')" v-bind="attrs" v-on="on">
                <v-icon>
                  mdi-folder
                </v-icon>

              </v-btn>
            </template>
            <span>sort project by title</span>
          </v-tooltip>
        </v-flex>

        <v-flex lg2 md2 sm6>
          <v-tooltip top>
            <template v-slot:activator="{ on, attrs }">
              <v-btn icon x-large @click="sortBy('person')" v-bind="attrs" v-on="on">
                <v-icon>
                  mdi-account
                </v-icon>

              </v-btn>
            </template>
            <span>sort project by person</span>
          </v-tooltip>
        </v-flex>
      </v-layout>

      <v-card class="pa-5 my-1" v-for="project in projects" :key="project.title">
        <v-layout row wrap :class="`project ${project.status}`">
          <v-flex xs12 md6>
            <div class=" caption grey--text">project title</div>
            <div>{{ project.title }}</div>
          </v-flex>
          <v-flex xs4 md2>
            <div class="caption grey--text">person</div>
            <div>{{ project.person }}</div>
          </v-flex>
          <v-flex xs4 md2>
            <div class="caption grey--text">due by</div>
            <div>{{ project.dueBy }}</div>
          </v-flex>
          <v-flex xs4 md2>
            <v-chip small class="mt-2" :color="project.color">
              {{ project.status }}
            </v-chip>

          </v-flex>
        </v-layout>
      </v-card>
    </v-container>
  </div>
</template>

<script>


export default {
  name: 'Dashboard',
  components: {},
  data() {
    return {
      'projects': [
        {'title': 'First project', 'person': 'person 1', 'dueBy': '1st Jan 2003', 'status': 'ongoing', 'color': 'red'},
        {
          'title': 'Second project',
          'person': 'person 2',
          'dueBy': '5st Feb 2013',
          'status': 'complete',
          'color': 'green'
        },
        {
          'title': 'Third project',
          'person': 'person 3',
          'dueBy': '22st Aug 2003',
          'status': 'overdue',
          'color': 'orange'
        },
        {
          'title': 'Fourth project',
          'person': 'person 4',
          'dueBy': '14st Jul 2006',
          'status': 'complete',
          'color': 'green'
        },
      ]
    }
  },
  methods: {
    sortBy(prop) {
      this.projects.sort((a, b) => (a[prop] < b[prop] ? -1 : 1))
    }
  }
}
</script>

<style>
.project.ongoing {
  border-left: 3px solid red;
}

.project.complete {
  border-left: 3px solid green;
}

.project.overdue {
  border-left: 3px solid orange;
}


</style>
