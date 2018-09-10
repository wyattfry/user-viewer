<template>
  <div id="app">
    <h1>Users</h1>
    <UserTable :users="users" v-on:rowClick="handleRowClick"/>
    <Modal :user="selectedUser" />
  </div>
</template>

<script>
import UserTable from './components/UserTable.vue';
import Modal from './components/Modal.vue';

const testUsers = [
  {
    'id': 1,
    'name': 'Leanne Graham',
    'username': 'Bret',
    'email': 'Sincere@april.biz',
    'address': {
      'street': 'Kulas Light',
      'suite': 'Apt. 556',
      'city': 'Gwenborough',
      'zipcode': '92998-3874',
      'geo': {
        'lat': '-37.3159',
        'lng': '81.1496',
      }
    },
    'phone': '1-770-736-8031 x56442',
    'website': 'hildegard.org',
    'company': {
      'name': 'Romaguera-Crona',
      'catchPhrase': 'Multi-layered client-server neural-net',
      'bs': 'harness real-time e-markets',
    }
  },
  {
    'id': 2,
    'name': 'Ervin Howell',
    'username': 'Antonette',
    'email': 'Shanna@melissa.tv',
    'address': {
      'street': 'Victor Plains',
      'suite': 'Suite 879',
      'city': 'Wisokyburgh',
      'zipcode': '90566-7771',
      'geo': {
        'lat': '-43.9509',
        'lng': '-34.4618',
      }
    },
    'phone': '010-692-6593 x09125',
    'website': 'anastasia.net',
    'company': {
      'name': 'Deckow-Crist',
      'catchPhrase': 'Proactive didactic contingency',
      'bs': 'synergize scalable supply-chains',
    },
  }
];

export default {
  name: 'app',
  components: {
    UserTable,
    Modal,
  },
  mounted: function() {
    httpGetAsync('https://jsonplaceholder.typicode.com/users', (res) => {this.users = JSON.parse(res)});
  },
  data: () => ({
    users: testUsers,
    selectedUser: testUsers[0],
  }),
  methods: {
    handleRowClick: function(id){
      this.selectedUser = this.users.filter(u=>u.id==id)[0];
    },
  },
};

function httpGetAsync(theUrl, callback) {
  var xmlHttp = new XMLHttpRequest();
  xmlHttp.onreadystatechange = function () {
    if (xmlHttp.readyState == 4 && xmlHttp.status == 200)
      callback(xmlHttp.responseText);
  }
  xmlHttp.open("GET", theUrl, true); // true for asynchronous 
  xmlHttp.send(null);
}

</script>
<style>
#app {
  text-align: center;
  margin-top: 40px;
}
</style>