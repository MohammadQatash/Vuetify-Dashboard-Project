<template>
  <div class="projects">
    <h1 class="subheading grey--text">Project</h1>
      <v-container>
        <v-row class="mb-4">
          <v-tooltip bottom>
            <template v-slot:activator="{ on }">
              <v-btn small outlined color="green" @click="sortByTitle('title')" class="mr-2" v-on="on">
                <v-icon left small>folder</v-icon>
                  <span class="caption text-lowercase">By project title</span>
              </v-btn>
            </template>
            <span>Sort project</span>
          </v-tooltip>

          <v-tooltip bottom>
            <template v-slot:activator="{ on }">
              <v-btn small outlined color="blue" @click="sortByName('person')" class="mr-2" dark v-on="on">
                <v-icon left small>person</v-icon>
                  <span class="caption text-lowercase">By name</span>
              </v-btn>
            </template>
            <span>Sort person</span>
          </v-tooltip>
        </v-row>

        <v-card flat  v-for="project in projects" :key="project.title" class="mb-1">
          <v-row :class="`pa-3 project ${project.status}`">
            <v-col class="ma-0 pa-0" cols="12" md='6'>
              <div class="caption grey--text">Project title</div>
              <div >{{project.title}}</div>
            </v-col>
            <v-col class="ma-0 pa-0" cols="12" md='3' sm='3'>
              <div class="caption grey--text">Person</div>
              <div >{{project.person}}</div>
            </v-col>
            <v-col class="ma-0 pa-0" cols="12" md='3' sm='3'>
              <div class="caption grey--text">Due By</div>
              <div >{{project.due}}</div>
            </v-col>
          </v-row>
        </v-card>
      </v-container>
  </div>
</template>

<script>
export default {
  name: 'projects',

  data: () => ({
    projects : [
      {title: 'Site web ', person :'Khaled', due: '10/10/1987', status:'no'},
      {title: 'Application mobile', person :'Iyad', due: '02/07/1990', status:'complete'},
      {title: 'Gestion de stock', person :'Zineb', due: '01/05/1987', status:'yes'},
      {title: 'Conception', person :'Hu Java', due: '02/09/1991', status:'up'},
    ]
  }),
  methods: {
    sortByTitle(prop){
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1:1)
    },
    sortByName(prop) {
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1:1)
    }
  }
}
</script>
<style >
  .project.complete {
    border-left: 4px solid #3cd1c2;
  }
  .project.no {
    border-left: 4px solid orange;
  }
  .project.up {
    border-left: 4px solid red;
  }
  .project.yes {
    border-left: 4px solid yellow;
  }
</style>
