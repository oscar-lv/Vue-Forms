<template>
<div class="container">
  <vue-particles class="background" color="#FF3232" :particleOpacity="0.75" :particlesNumber="200" shapeType="circle" :particleSize="3" linesColor="#FF3232" :linesWidth="0.55" :lineLinked="true" :lineOpacity="0.75" :linesDistance="75" :moveSpeed="3" :hoverEffect="false"
    :clickEffect="false" />
  <br>
  <br>
  <h1 style="text-align:center"> Please Complete </h1>
  <form id="center" v-if="!submitted">
    <div class="row">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="form-group">
          <label> First Name </label>
          <input v-model="forename" type="text" class="form-control">
        </div>
        <div class="form-group">
          <label> Last Name </label>
          <input v-model="surname" type="text" class="form-control">
        </div>
        <div class="form-group">
          <label> Age </label>
          <basic-select :options="options" :selected-option="item" placeholder="select item" @select="onSelect">
          </basic-select>
        </div>
        <div class="form-group">
          <label> Email </label>
          <input v-model.lazy="email" type="text" class="form-control">
        </div>
        <div class="form-group">
          <label> Password </label>
          <input v-model="password" type="password" class="form-control">
        </div>
        <div class="form-group">
          <p> Store Data ?</p>
          <label>
                  <input v-model="store" type="radio" value="Yes"> Yes
              </label>
          <label>
                   <input v-model="store" type="radio" value="No"> No
              </label>
        </div>
        <button type="submit" class="btn btn-warning" @click.prevent="submitted=true"> Submit </button>
      </div>
    </div>
  </form>
  <div v-if="submitted" class="row">
    <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
      <div class="panel panel-default">
        <div class="panel-heading">
          <h4>Your Data</h4>
        </div>


        <div class="panel-body">
          <p>Full Name: {{forename + ' ' + surname}} </p>
          <p>Mail: {{email}}</p>
          <p>Password: {{password}} </p>
          <p>Store in Database?: {{store}} </p>
          <p>Age : {{item.value}}</p>
        </div>
      </div>
    </div>
  </div>

</div>
</template>

<script>
import {
  BasicSelect
} from 'vue-search-select'

export default {
  data() {
    return {
      forename: '',
      surname: '',
      email: '',
      password: '',
      store: '',
      submitted: false,
      age : '',
      options: [{
          value: '18',
          text: '18'
        },
        {
          value: '19',
          text: '19'
        },
        {
          value: '20',
          text: '20'
        },
        {
          value: '21',
          text: '21'
        },
        {
          value: '22',
          text: '22'
        }
      ],
      searchText: '', // If value is falsy, reset searchText & searchItem
      item: {
        value: '',
        text: ''
      }
    }
  },
  methods: {
    onSelect(item) {
      this.item = item
    },
    reset() {
      this.item = {}
    },
    selectOption() {
      // select option from parent component
      this.item = this.options[0]
    }
  },
  components: {
    BasicSelect
  },
}
</script>

<style>
.background {
  position: absolute;
  background-size: cover;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  overflow-y: hidden;
  z-index: 0;
}

#center {

  height: 50%;

  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  margin: auto;
}
</style>
