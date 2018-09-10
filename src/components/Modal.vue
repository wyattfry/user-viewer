<template>
  <div class="modal fade" id="userDetailModal" tabindex="-1" role="dialog">
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title" id="exampleModalLabel">{{ user.name }}</h4>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <h6>User Details</h6>
            <table v-if="user" class="table table-borderless table-sm">
              <tbody>
                <tr><td><h6>ID</h6></td><td class="id">{{ user.id }}</td></tr>
                <tr><td><h6>Username</h6></td><td class="username">{{ user.username }}</td></tr>
                <tr>
                  <td>
                    <h6>Email</h6></td><td class="email"><a target="_blank" :href="'mailto:' + user.email">{{ user.email }}</a>
                  </td>
                </tr>
                <tr>
                  <td>
                    <h6>Address</h6></td><td class="address">
                      <address>
                        <span v-for="line in Object.values(user.address).slice(0,4)" :key="line">{{ line }}<br></span>
                      </address>
                  </td>
                </tr>
                <tr>
                  <td>
                    <h6>Coordinates</h6></td><td class="latlng">
                    <a target="_blank" :href="'https://www.google.com/maps/?q=' + Object.values(user.address.geo).join()">{{ Object.values(user.address.geo).join(', ') }}</a>
                  </td>
                </tr>
                <tr><td><h6>Phone</h6></td><td class="phone"><a :href="'tel:' + user.phone">{{ user.phone }}</a></td></tr>
                <tr><td><h6>Website</h6></td><td class="website"><a target="_blank" :href="'http://' + user.website">{{ user.website }}</a></td></tr>
                <tr>
                  <td><h6>Company</h6></td><td class="company">
                    <p class="company-name">{{ user.company.name }}</p>
                    <span>&#8220;{{ user.company.catchPhrase }}&#8221;<br></span>
                    <span><em>{{ user.company.bs }}</em><br></span>
                  </td
                ></tr>
              </tbody>
            </table>
          </div>
        </div>
      </div>
    </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    user: Object,
  },
};
</script>
<style>
#userDetailModal {
  text-align: left;
}
p.company-name {
  margin-bottom: 0.5rem; 
}
tr h6{
  text-align:right;
  line-height: 1.5;
}
</style>