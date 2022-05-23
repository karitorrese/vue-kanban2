<template>
  <div class="container mt-5">
    <div class="row">
      <div class="col form-inline">
        <b-form-input v-model="newTask" placeholder="Enter Task" @keyup.enter="add"></b-form-input> <b-button class="ml-2" variant="primary" @click="add">add</b-button>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col-md-3">
        <div class="p-2 alert alert-secondary">
          <h3>Backlog</h3>
          <draggable class="list-group" :list="arrBacklog" group="tasks">
            <div class="list-group-items" v-for="element in arrBacklog" :key="element.name">
              <b-card
              tag="article"
              style="max-width: 20rem;"
              class="mb-2"
              >
                <b-card-text>
                  {{element.name}}
                </b-card-text>
              </b-card>
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-primary">
          <h3>In Progress</h3>
          <draggable class="list-group" :list="arrInProgress" group="tasks">
            <div class="list-group-items" v-for="element in arrInProgress" :key="element.name">
              <b-card
              tag="article"
              style="max-width: 20rem;"
              class="mb-2"
              >
                <b-card-text>
                  {{element.name}}
                </b-card-text>
              </b-card>
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-warning">
          <h3>Tested</h3>
          <draggable class="list-group" :list="arrTested" group="tasks">
            <div class="list-group-items" v-for="element in arrTested" :key="element.name">
              <b-card
              tag="article"
              style="max-width: 20rem;"
              class="mb-2"
              >
                <b-card-text>
                  {{element.name}}
                </b-card-text>
              </b-card>
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert alert-success">
          <h3>Done</h3>
          <draggable class="list-group" :list="arrDone" group="tasks">
            <div class="list-group-items" v-for="element in arrDone" :key="element.name">
              <b-card
              tag="article"
              style="max-width: 20rem;"
              class="mb-2"
              >
                <b-card-text>
                  {{element.name}}
                </b-card-text>
              </b-card>
            </div>
          </draggable>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from "vuedraggable"

export default {
  name: 'App',
  components: {
    draggable
  },
  data() {
    return {
      newTask: "",
      arrBacklog: [
        {name: "Code SignUpPage"},
        {name: "Test Dash"},
        {name: "Style Reg"},
        {name: "Help with designs"}
      ],
      arrInProgress: [],
      arrTested: [],
      arrDone: []
    }
  },
  methods:{
    add() {
      if(this.newTask){
        this.arrBacklog.push({name: this.newTask});
        this.newTask = "";
      }
    }
  }
}
</script>

<style>
</style>
