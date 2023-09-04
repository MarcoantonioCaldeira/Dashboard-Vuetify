<template>
  <v-app>
    <v-navigation-drawer v-model="isDrawerOpen">
      <v-list>
        <v-list-subheader>Menu</v-list-subheader>
        <v-list-item prepend-icon="mdi-home">Home</v-list-item>
        <v-list-item prepend-icon="mdi-account">Users</v-list-item>

        <v-list-group value="Customers">
          <template #activator="{ props }">
            <v-list-item 
              v-bind="props"
              prepend-icon="mdi-account-circle"
            >Customers</v-list-item>
          </template>

          <v-list-item prepend-icon="mdi-currency-usd">Sales</v-list-item>
          <v-list-item prepend-icon="mdi-chart-line">Report</v-list-item>
        </v-list-group>
      </v-list>
    </v-navigation-drawer>
    
    <v-app-bar flat class="border-b">
      <v-app-bar-nav-icon @click="isDrawerOpen = !isDrawerOpen"></v-app-bar-nav-icon>
      <v-app-bar-title>Meu app</v-app-bar-title>

      <template #append>
        <v-btn icon class="mr-2">
          <v-badge dot color="info">
            <v-icon icon="mdi-bell-outline"></v-icon>
          </v-badge>
        </v-btn>

        <v-menu>
          <template #activator="{ props }">
            <v-avatar v-bind="props">
              <v-img  
              cover 
              src="https://www.cnnbrasil.com.br/wp-content/uploads/sites/12/2022/01/272659509_640826040498160_305754906527072885_n-e1643549776803.jpg?w=876&h=484&crop=1"></v-img>
            </v-avatar>
          </template>

          <v-card min-width="200px">
            <v-list :list="false" density="compact"  nav>
              <v-list-item 
                prepend-icon="mdi-account-outline">
                <v-list-item-title>My profile</v-list-item-title>
              </v-list-item>
              <v-list-item prepend-icon="mdi-heart-outline">
                <v-list-item-title>Favorites</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-menu>
      </template>
    </v-app-bar>
    <v-main>
        <v-container>
          <h1 class="mb-6">Dashboard</h1>
          <v-card flat class="border mb-4">

          </v-card>
          <v-card-title>Last Users</v-card-title>

          <v-card-title>
            <v-btn @click="isDialogOpen = true" variant="tonal" size="small">Add User</v-btn>

            <v-dialog
                v-model="isDialogOpen"
                width="600px"
              >
              <v-card>
                <v-card-title>Add User</v-card-title>
                <v-card-text>
                  <v-row>
                    <v-col>
                      <v-text-field 
                        label="Nome" 
                        variant="outlined"
                        :rules="emailRules"
                        ></v-text-field>
                    </v-col>

                    <v-col>
                      <v-text-field 
                        label="Email"
                        variant="outlined"
                        :rules="emailRules"
                         ></v-text-field>
                    </v-col>
                  </v-row>

                  <v-select 
                    label="Position" 
                    variant="outlined"
                    :items="['Admin', 'Manager', 'Guest']"
                  >

                  </v-select>
                </v-card-text>

                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn variant="text" @click="isDialogOpen = false">Cancel</v-btn>
                  <v-btn variant="tonal" color="success">Save</v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
          </v-card-title>

          <v-table>
            <thead>
              <tr>
                <th>Name</th>
                <th>E-mail</th>
                <th>Office</th>
                <th>Actions</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Name-User</td>
                <td>user@gmail.com</td>
                <td>
                  <v-chip color="primary" variant="outlined" size="small">Admin</v-chip>
                </td>
                <td>
                  <v-btn variant="tonal" color="primary">Edit</v-btn>
                </td>
              </tr>
              <tr>
                <td>Name-User</td>
                <td>user@gmail.com</td>
                <td>
                  <v-chip variant="outlined" size="small">Guest</v-chip>
                </td>
                <td>
                  <v-btn variant="tonal" color="primary">Edit</v-btn>
                </td>
              </tr>
            </tbody>
          </v-table>
          <v-row>
            <v-col cols="12" sm="6"  md="4" lg="3">
              <v-card flat class="border">
                <v-img class="align-end text-white" src="https://images.pexels.com/photos/2748019/pexels-photo-2748019.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1">
                  <v-card-title>Top 10 places in Italy</v-card-title>
                </v-img>
                
                <v-card-subtitle class="pt-3">Venice</v-card-subtitle>

                <v-card-text>
                  <div>City of Venice,</div>
                  <div>one of the most visited places in the world</div>
                </v-card-text>

                <v-card-actions>
                  <v-btn  variant="outlined" color="primary">See more</v-btn>
                  <v-btn  prepend-icon="mdi-cart" variant="tonal" color="primary">Buy Ticket</v-btn>
                </v-card-actions>
              </v-card>
            </v-col>

            <v-col cols="12" sm="6" md="4" lg="3">
              <v-card flat class="border">
                <v-img class="align-end text-white" src="https://images.unsplash.com/photo-1503220317375-aaad61436b1b?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxleHBsb3JlLWZlZWR8MTB8fHxlbnwwfHx8fHw%3D&w=1000&q=80">
                  <v-card-title>Best travel tips</v-card-title>
                </v-img>
                
                <v-card-subtitle class="pt-3">Travels</v-card-subtitle>

                <v-card-text>       
                  <div>The most visited destinations in the world</div>
                </v-card-text>

                <v-card-actions>
                  <v-btn  variant="outlined" color="primary">See more</v-btn>
                  <v-btn  prepend-icon="mdi-cart" variant="tonal" color="primary">Buy Ticket</v-btn>
                </v-card-actions>
              </v-card>
            </v-col>

            <v-col cols="12" sm="6" md="4" lg="3">
              <v-card flat class="border">
                <v-img class="align-end text-white" src="https://www.vaipradisney.com/blog/wp-content/uploads/2021/06/disney-aniversario-50-anos-capa.jpg">
                  <v-card-title>Top 10 best Disney attractions</v-card-title>
                </v-img>
                
                <v-card-subtitle class="pt-3">Disney Park</v-card-subtitle>

                <v-card-text>
                  <div></div>
                  <div>One of the most visited places in the world and with the best attractions</div>
                </v-card-text>

                <v-card-actions>
                  <v-btn  variant="outlined" color="primary">See more</v-btn>
                  <v-btn  prepend-icon="mdi-cart" variant="tonal" color="primary">Buy Ticket</v-btn>
                </v-card-actions>
              </v-card>
            </v-col>
           
          </v-row>
        </v-container>
    </v-main>
  </v-app>
</template>

<script setup>
  import { ref } from 'vue';

  const isDrawerOpen = ref(false)
  const isDialogOpen = ref(false)
  const emailRules = [
    values => {
      if(value) return true;

      return 'Required Email'
      
    },

    value => {
      if(value.includes('@')) return true;

      return 'Invalid Email'
    }


    
  ]

</script>
