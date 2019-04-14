<template>
  <div class="hello">
    <div class="container">
      <div class="row">
        <div class="col-md-8 col-md-offset-2">
         <img style="width:50px; height: 50px" src="./img/blood.png"> <h1 class="page-header">Blood Donation Record System 

            <img :src="user.avatarUrl() ? user.avatarUrl() : '/avatar-placeholder.png'" class="avatar">
            <small><span class="sign-out">(<a href="#" @click.prevent="signOut">Sign Out</a>)</span></small>
          </h1>
          <h2 class="user-info">
            <small>
              Blood Donation Ledger
            </small>
            <small class="pull-right">
            {{ user.username ? user.username : user.identityAddress }}
            </small>

          </h2>
          <form @submit.prevent="addTodo" :disabled="! donorfn">
            <div class="input-group">
              <p>Donor First Name</p>
              <input v-model="todo" type="text" class="form-control" placeholder="edit me" autofocus>
              <p>Donor Middle Name</p>
              <input v-model="donorfn" class="form-control" style="color: black" placeholder="edit me" autofocus><br><br>
              <p>Donor Last Name</p>
              <input v-model="donorln" class="form-control" style="color: black" placeholder="edit me" autofocus><br>
               <p>Donor Occupation</p>
              <input v-model="donorocc" class="form-control" style="color: black" placeholder="edit me" autofocus><br>
               <p>Donor Phone</p>
              <input v-model="donorph" class="form-control" style="color: black" placeholder="edit me" autofocus><br>
               <p>Donor Address</p>
              <textarea v-model="donoradd"  class="form-control" style="color: black" placeholder="add address"></textarea>
               <p>Donor Email</p>
              <input v-model="donorem" class="form-control" style="color: black" placeholder="@email.com" autofocus><br>
              <p>Donor Blood Type</p>

              <input v-model="donortyp" class="form-control" style="color: black" placeholder="example: O+" autofocus><br>
               <p>Blood Amount Donated</p>
              <input v-model="donoramt" class="form-control" style="color: black" placeholder="edit me" autofocus><br>
              <p>Last Time Blood Donated</p>
              <input v-model="donorldt" class="form-control" style="color: black" placeholder="edit me" autofocus>
              <br>
              <br>
              <span class="input-group-btn">
                <button class="btn btn-default" style="opacity: 0"></button>
              </span>
          </div>
          <span class="input-group-btn">
    <button class="btn btn-default" type="submit" :disabled="! donorem">Add</button>
              </span>

        </form>
<br> </div>


      <table>

<div ><img style="width: 70px; height: 70px; text-align: center;" src="./img/blood-donate.png">
<p style="font-family: Courier; font-size: 15pt; color: white">Blood Donors</p>
</div>
        <tr>

        <th>First Name</th>
        <th>Middle Name</th>
        <th>Last Name</th>
        <th>Occupation</th>
        <th>Phone</th>
        <th>Address</th>
        <th>Email</th>
        <th>Blood Type</th>
        <th>Amount Donated</th>
        <th>Last Donation Date</th>
        <tr>
        <tr>
          <td>
            <div v-for="todo in todos"
              class="list-group-item"
              :class="{completed: todo.completed}"
              :key="todo.id">
              <label>
                <p type="text">{{ todo.text }}</p>
              </label>
             
            </div>

        <td>
            <div v-for="donorfn in donorfname"
                class="list-group-item"
                :class="{completed: donorfn.completed}"
                :key="donorfn.id">
                <label>
                  <p type="text">{{ donorfn.text }}</p>
                </label>
                <!--- Below snippet allows us to delete records if used correctly-->
              <!--  <a @click.prevent="donorfname.splice(donorfname.indexOf(donorfn), 1)"
                class="delete pull-right"
                href="#">X</a>-->
            </div>
        </td>
        <td>
            <div v-for="donorln in donorlname"
                class="list-group-item"
                :class="{completed: donorln.completed}"
                :key="donorln.id">
                <label>
                  <p type="text" >{{ donorln.text }}</p>
                </label>
             
              </div>
        </td>
      
        <td>

            <div v-for="donorocc in donoroccupation"
                class="list-group-item"
                :class="{completed: donorocc.completed}"
                :key="donorocc.id">
                <label>
                  <p type="text" >{{ donorocc.text }}</p>
                </label>
           
              </div>
        </td>
     
        <td>

            <div v-for="donorph in donorphone"
                class="list-group-item"
                :class="{completed: donorph.completed}"
                :key="donorph.id">
                <label>
                  <p type="text">{{ donorph.text }}</p>
                </label>
              
              </div>
        </td>
     
        <td>

            <div v-for="donoradd in donoraddress"
                class="list-group-item"
                :class="{completed: donoradd.completed}"
                :key="donoradd.id">
                <label>
                  <p type="text">{{ donoradd.text }}</p>
                </label>
              
              </div>
        </td>
     
        <td>

            <div v-for="donorem in donoremail"
                class="list-group-item"
                :class="{completed: donorfn.completed}"
                :key="donorem.id">
                <label>
                  <p type="text" >{{ donorem.text }}</p>
                </label>
           
              </div>
        </td>
     
        <td>

            <div v-for="donortyp in donortype"
                class="list-group-item"
                :class="{completed: donortyp.completed}"
                :key="donortyp.id">
                <label>
                  <p type="text">{{ donortyp.text }}</p>
                </label>
         
              </div>
        </td>
     
        <td>

            <div v-for="donoramt in donoramount"
                class="list-group-item"
                :class="{completed: donoramt.completed}"
                :key="donoramt.id">
                <label>
                  <p type="text">{{ donoramt.text }}</p>
                </label>
             
              </div>
        </td>
      
        <td>

            <div v-for="donorldt in donorlastd"
                class="list-group-item"
                :class="{completed: donorldt.completed}"
                :key="donorldt.id">
                <label>
                  <p type="text" >{{ donorldt.text }}</p>
                </label>
             
              </div>
         </td>
       </tr>
        </table><br><br>
       
      </div>
    </div>
  </div>
</template>

<script>
var STORAGE_FILE = 'todos.json'
var STORE_NAME = 'donorfname.json'
var STORE_LNAME = 'donorlname.json'
var STORE_OCC = 'donoroccupation.json'
var STORE_ADRS = 'donoraddress.json'
var STORE_PHONE = 'donorphone.json'
var STORE_BAMT = 'donoramount.json'
var STORE_EMAIL = 'donoremail.json'
var STORE_TYPE = 'donortype.json'
var STORE_LASTTD = 'donorlastd.json'

export default {
  name: 'dashboard',
  props: ['user'],
  data () {
    return {
      blockstack: window.blockstack,
      todos: [],
      todo: '',
      donorfname: [],
      donorfn: '',
      donorlname: [],
      donorln: '',
      donoroccupation: [],
      donorocc: '',
      donorphone: [],
      donorph: '',
      donoraddress: [],
      donoradd: '',
      donoremail: [],
      donorem: '',
      donortype: [],
      donortyp: '',
      donoramount: [],
      donoramt: '',
      donorlastd: [],
      donorldt: '',
      uidCount: 0
    }
  },
  watch: {
    todos: {
      handler: function (todos) {
        const blockstack = this.blockstack

        // encryption is now enabled by default
        return blockstack.putFile(STORAGE_FILE, JSON.stringify(todos))
      },
      deep: true
    },
    donorfname: {
      handler: function (donorfname) {
        const blockstack = this.blockstack

        // encryption is now enabled by default
        return blockstack.putFile(STORE_NAME, JSON.stringify(donorfname))
      },
      deep: true
    },
    donorlname: {
      handler: function (donorlname) {
        const blockstack = this.blockstack

        // encryption is now enabled by default
        return blockstack.putFile(STORE_LNAME, JSON.stringify(donorlname))
      },
      deep: true
    },
    donoroccupation: {
      handler: function (donoroccupation) {
        const blockstack = this.blockstack

        // encryption is now enabled by defult
        return blockstack.putFile(STORE_OCC, JSON.stringify(donoroccupation))
      },
      deep: true
    },
    donorphone: {
      handler: function (donorphone) {
        const blockstack = this.blockstack

        // encryption is now enabled by default
        return blockstack.putFile(STORE_PHONE, JSON.stringify(donorphone))
      },
      deep: true
    },
    donoraddress: {
      handler: function (donoraddress) {
        const blockstack = this.blockstack

        // encryption is now enabled by default
        return blockstack.putFile(STORE_ADRS, JSON.stringify(donoraddress))
      },
      deep: true
    },
    donoremail: {
      handler: function (donoremail) {
        const blockstack = this.blockstack

        // encryption is now enabled by default
        return blockstack.putFile(STORE_EMAIL, JSON.stringify(donoremail))
      },
      deep: true
    },
    donortype: {
      handler: function (donortype) {
        const blockstack = this.blockstack

        // encryption is now enabled by default
        return blockstack.putFile(STORE_TYPE, JSON.stringify(donortype))
      },
      deep: true
    },
    donoramount: {
      handler: function (donoramount) {
        const blockstack = this.blockstack

        // encryption is now enabled by default
        return blockstack.putFile(STORE_BAMT, JSON.stringify(donoramount))
      },
      deep: true
    },
    donorlastd: {
      handler: function (donorlastd) {
        const blockstack = this.blockstack

        // encryption is now enabled by default
        return blockstack.putFile(STORE_LASTTD, JSON.stringify(donorlastd))
      },
      deep: true
    }

  },
  mounted () {
    this.fetchData()
  },
  methods: {
    addTodo () {
      if (!this.todo.trim()) {
        return
      }
      this.todos.unshift({
        id: this.uidCount++,
        text: this.todo.trim(),
        completed: false
      })
      this.todo = ''

      if (!this.donorfn.trim()) {
        return
      }
      this.donorfname.unshift({
        id: this.uidCount++,
        text: this.donorfn.trim(),
        completed: false
      })
      this.donorfn = ''

      if (!this.donorln.trim()) {
        return
      }
      this.donorlname.unshift({
        id: this.uidCount++,
        text: this.donorln.trim(),
        completed: false
      })
      this.donorln = ''

      if (!this.donorocc.trim()) {
        return
      }
      this.donoroccupation.unshift({
        id: this.uidCount++,
        text: this.donorocc.trim(),
        completed: false
      })
      this.donorocc = ''

      if (!this.donorph.trim()) {
        return
      }
      this.donorphone.unshift({
        id: this.uidCount++,
        text: this.donorph.trim(),
        completed: false
      })
      this.donorph = ''

      if (!this.donoradd.trim()) {
        return
      }
      this.donoraddress.unshift({
        id: this.uidCount++,
        text: this.donoradd.trim(),
        completed: false
      })
      this.donoradd = ''

      if (!this.donorem.trim()) {
        return
      }
      this.donoremail.unshift({
        id: this.uidCount++,
        text: this.donorem.trim(),
        completed: false
      })
      this.donorem = ''

      if (!this.donortyp.trim()) {
        return
      }
      this.donortype.unshift({
        id: this.uidCount++,
        text: this.donortyp.trim(),
        completed: false
      })
      this.donortyp = ''

      if (!this.donoramt.trim()) {
        return
      }
      this.donoramount.unshift({
        id: this.uidCount++,
        text: this.donoramt.trim(),
        completed: false
      })
      this.donoramt = ''

      if (!this.donorldt.trim()) {
        return
      }
      this.donorlastd.unshift({
        id: this.uidCount++,
        text: this.donorldt.trim(),
        completed: false
      })
      this.donorldt = ''
    },

    fetchData () {
      const blockstack = this.blockstack
      blockstack.getFile(STORAGE_FILE) // decryption is enabled by default
      .then((todosText) => {
        var todos = JSON.parse(todosText || '[]')
        todos.forEach(function (todo, index) {
          todo.id = index
        })

        this.uidCount = todos.length
        this.todos = todos
      })

      blockstack.getFile(STORE_NAME) // decryption is enabled by default
      .then((donorfnameText) => {
        var donorfname = JSON.parse(donorfnameText || '[]')
        donorfname.forEach(function (donorfn, index) {
          donorfn.id = index
        })

        this.uidCount = donorfname.length
        this.donorfname = donorfname
      })

      blockstack.getFile(STORE_LNAME) // decryption is enabled by default
      .then((donorlnameText) => {
        var donorlname = JSON.parse(donorlnameText || '[]')
        donorlname.forEach(function (donorln, index) {
          donorln.id = index
        })

        this.uidCount = donorlname.length
        this.donorlname = donorlname
      })
      blockstack.getFile(STORE_OCC) // decryption is enabled by default
      .then((donoroccupationText) => {
        var donoroccupation = JSON.parse(donoroccupationText || '[]')
        donoroccupation.forEach(function (donorocc, index) {
          donorocc.id = index
        })

        this.uidCount = donoroccupation.length
        this.donoroccupation = donoroccupation
      })

      blockstack.getFile(STORE_PHONE) // decryption is enabled by default
      .then((donorphoneText) => {
        var donorphone = JSON.parse(donorphoneText || '[]')
        donorphone.forEach(function (donorph, index) {
          donorph.id = index
        })

        this.uidCount = donorphone.length
        this.donorphone = donorphone
      })

      blockstack.getFile(STORE_ADRS) // decryption is enabled by default
      .then((donoraddressText) => {
        var donoraddress = JSON.parse(donoraddressText || '[]')
        donoraddress.forEach(function (donoradd, index) {
          donoradd.id = index
        })

        this.uidCount = donoraddress.length
        this.donoraddress = donoraddress
      })
      blockstack.getFile(STORE_EMAIL) // decryption is enabled by default
      .then((donoremailText) => {
        var donoremail = JSON.parse(donoremailText || '[]')
        donoremail.forEach(function (donorem, index) {
          donorem.id = index
        })

        this.uidCount = donoremail.length
        this.donoremail = donoremail
      })

      blockstack.getFile(STORE_BAMT) // decryption is enabled by default
      .then((donoramountText) => {
        var donoramount = JSON.parse(donoramountText || '[]')
        donoramount.forEach(function (donoramt, index) {
          donoramt.id = index
        })

        this.uidCount = donoramount.length
        this.donoramount = donoramount
      })

      blockstack.getFile(STORE_TYPE) // decryption is enabled by default
      .then((donortypeText) => {
        var donortype = JSON.parse(donortypeText || '[]')
        donortype.forEach(function (donortyp, index) {
          donortyp.id = index
        })

        this.uidCount = donortype.length
        this.donortype = donortype
      })

      blockstack.getFile(STORE_LASTTD) // decryption is enabled by default
      .then((donorlastdText) => {
        var donorlastd = JSON.parse(donorlastdText || '[]')
        donorlastd.forEach(function (donorldt, index) {
          donorldt.id = index
        })

        this.uidCount = donorlastd.length
        this.donorlastd = donorlastd
      })
    },

    signOut () {
      this.blockstack.signUserOut(window.location.href)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>

input::placeholder {
  color: grey;
}
table {
  font-family: Courier, sans-serif;
  border-collapse: collapse;
  width: 100%;
  color: black;

}

td {
  border: 1px solid grey;
  text-align: left;
}
th{
    border: 3px solid grey;

  text-align: center;
}

tr:nth-child(even) {
  background-color: #f2eeea;
}

</style>
