<template>
  <div class="home pa-6">
    <v-list
      subheader
      two-line
      flat
      class="pt-0"
    >
      <div
        v-for="task in tasks"
        :key="task.id"
      >
        <v-list-item
          @click="doneTask(task.id)"
          :class="{'grey lighten-2': task.done}"
        >
          <template v-slot:default="{ active, }">
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
                :class="{'text-decoration-line-through': task.done}"
              >
                {{ task.title }}
              </v-list-item-title>
              <v-list-item-subtitle>S/ {{ task.price }}</v-list-item-subtitle>
            </v-list-item-content>
          </template>
        </v-list-item>
        <v-divider></v-divider>
      </div>
    </v-list>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: 'Home',
  components: {
    
  },
  data() {
    return {
      tasks: [
        {
          id: 1,
          title: 'Salchipapa',
          price: 6.5,
          done: false
        },
        {
          id: 2,
          title: 'Hamburguesa',
          price: 5.5,
          done: true
        },
        {
          id: 3,
          title: 'Broaster',
          price: 7.9,
          done: true
        }
      ]
    }
  },
  methods: {
    doneTask(id) {
      const task = this.tasks.filter(task => task.id == id)[0];
      task.done = !task.done;
    }
  },
}
</script>
