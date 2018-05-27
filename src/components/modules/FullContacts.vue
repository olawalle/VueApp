<template>
<transition name="el-zoom-in-top">
  <div class="Mymodal col-md-12">
    <contacts-list v-bind:contacts="contacts"></contacts-list>
      <div class="col-md-12">
        <div class="add pull-right">
          <span class="secondary-btn" a href="#" title="enter details" data-toggle="modal" data-target="#myModal"><i class="fa fa-pencil"></i></span>
          <span class="secondary-btn" a href="#" title="Upload from file" data-toggle="modal" data-target="#mysecModal"><i class="fa fa-upload"></i></span>
            <a href="#">
              <div class="wrap-plus" title="Add new contact">+</div>
            </a>  
        </div>   
        <modal></modal>
          <!-- MODAL --> 
          <div class="modal fade" id="mysecModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel">
            <div class="modal-dialog" role="document">
              <div class="modal-content"> <a href="#"><h2 class="pull-right closebtn text-danger" data-dismiss="modal"><i class="fa fa-close"></i></h2></a>
              <form action="" class="contact">
              <h2 class="text-center"><b>Upload Contact</b></h2>
                <fieldset class="contact-inner">
                  <p class="contact-input">
                    <input type="file" name="upload" placeholder="Upload contact" >
                  </p>
                  <p class="contact-submit">
                    <input type="submit" data-dismiss="modal" v-on:click="createContact" value="Create Contact">
                  </p>
                </fieldset>
              </form>
              </div>
            </div>
          </div>       
          <div class="modal fade" id="myModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel">
            <div class="modal-dialog" role="document">
              <div class="modal-content"><a href="#"><h2 class="pull-right closebtn text-danger" data-dismiss="modal"><i class="fa fa-close"></i></h2></a>
                <form  @submit.prevent="validateBeforeSubmit" class="contact">
              <h2 class="text-center"><b>Add Contact</b></h2>
                <fieldset class="contact-inner">
                  <p class="contact-input">
                    <input type="text" v-validate="'required'" name="name" v-model="name" placeholder="Name" auofocus>
                    <div class="form-error" v-if="errors.has('name')">
                      {{ errors.first('name') }}
                     </div>
                  </p>
                  <p class="contact-input">
                    <input type="number" v-validate="'required'" name="number" v-model="number" placeholder="Number">
                    <div class="form-error" v-if="errors.has('number')">
                      {{ errors.first('number') }}
                    </div>
                  </p>
                  <p class="contact-input">
                    <input v-validate="'required'" name="email" v-model="email" placeholder="Email address" >
                    <div class="form-error" v-if="errors.has('email')">
                      {{ errors.first('email') }}
                    </div>
                  </p>
                  <p class="contact-input">
                    <select v-model="msn">
                      <option disabled value="">Has Messanger</option>
                      <option>True</option>
                      <option>False</option>
                    </select>
                  </p>
                  <p class="contact-input">
                    <select v-model="Group">
                      <option disabled value="">Group</option>
                      <option>Gold</option>
                      <option>Diamond</option>
                      <option>Platinum</option>
                    </select>
                  </p>  
                  <p class="contact-submit">
                  <button type="submit" :disabled="errors.any()" data-dismiss="modal" v-on:click="createContact" value="">Create Contact</button>
                </p>
              </fieldset>
            </form>
              </div>
            </div>
          </div>
          <div class="modal fade" id="myTrdModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel">
                    <div class="modal-dialog" role="document">
                    <div class="modal-content"><a href="#"><h2 class="pull-right closebtn text-danger" data-dismiss="modal"><i class="fa fa-close"></i></h2></a>
                        <div class="contact">
                        <h2 class="text-center"><b>Compose Notification</b></h2>
                            <ul class="nav nav-tabs">
                                <li class="active"><a data-toggle="tab" href="#home"><b>SMS</b></a></li>
                                <li><a data-toggle="tab" href="#menu1"><b>E-mail</b></a></li>
                            </ul>

                            <div class="tab-content">
                                <div id="home" class="tab-pane fade in active">
                                <form> 
                                    <fieldset class="contact-inner">
                                        <p class="contact-input">
                                            <input type="text"  name="From" placeholder="From:" auofocus>
                                        </p>
                                        <p class="contact-input">
                                            <input type="text"  name="number" placeholder="To:">
                                        </p>
                                        <p class="contact-input">
                                            <input type="text" name="Title" placeholder="Title:" >
                                        </p>
                                        <p class="contact-input">
                                        </p>
                                        <p class="contact-input">
                                            <textarea name="" id="" cols="30" rows="10"></textarea>
                                        </p> 
                                        <p class="schedule">
                                        <button type="submit" data-dismiss="modal" v-on:click="createContact" value="">Schedule message <i class="fa fa-calendar"></i></button>
                                        </p>
                                        <p class="contact-submit">
                                        <button type="submit" data-dismiss="modal" v-on:click="createContact" value="">Send SMS now</button>
                                        </p>
                                        <p class="draft">
                                        <button type="submit" data-dismiss="modal" v-on:click="createContact" value="">Save as draft</button>
                                        </p>
                                    </fieldset>
                                    </form>
                                </div>
                                <div id="menu1" class="tab-pane fade">
                                <form> 
                                    <fieldset class="contact-inner">
                                        <p class="contact-input">
                                            <input type="text"  name="name" v-model="name" placeholder="From:" auofocus>
                                        </p>
                                        <p class="contact-input">
                                            <input type="text"  name="number" v-model="number" placeholder="To:">
                                        </p>
                                        <p class="contact-input">
                                            <input type="text" name="address" v-model="address" placeholder="Title:" >
                                        </p>
                                        <p class="contact-input">
                                        </p>
                                        <p class="contact-input">
                                            <textarea name="" id="" cols="30" rows="10"></textarea>
                                        </p>
                                        <p class="schedule">
                                        <button type="submit" data-dismiss="modal" v-on:click="createContact" value="">Schedule message <i class="fa fa-calendar"></i> </button>
                                        </p>
                                        <p class="contact-submit">
                                        <button type="submit" data-dismiss="modal" v-on:click="createContact" value="">Send Email</button>
                                        </p> 
                                        <p class="draft">
                                        <button type="submit" data-dismiss="modal" v-on:click="createContact" value="">Save as draft</button>
                                        </p>
                                    </fieldset>
                                    </form>
                                </div>
                            </div>
                        </div>
                    </div>
                    </div>
                </div>
        </div>
  </div>
</transition>
</template>
<script>
import sweetalert from 'sweetalert'
import ContactsList from './contacts/ContactsList'
import Groups from './Groups'
export default {
  components: {
    ContactsList,
    Groups
  },
  data () {
    return {
      dialogTableVisible: false,
      dialogTableVisible2: false,
      name: '',
      number: '',
      email: '',
      Group: '',
      msn: '',
      contacts: [{
        name: 'Lanre Oyedotun',
        number: '0803220918',
        Group: 'Gold',
        email: 'lanre@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Lennie Mike',
        number: '0803220918',
        Group: 'Gold',
        email: 'lenie@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Sammie sam',
        number: '0803220918',
        Group: 'Gold',
        email: 'sammie@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Lennie Mike',
        number: '0803220918',
        Group: 'Gold',
        email: 'lenie@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Sammie sam',
        number: '0803220918',
        Group: 'Gold',
        email: 'sammie@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Lennie Mike',
        number: '0803220918',
        Group: 'Gold',
        email: 'lenie@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Sammie sam',
        number: '0803220918',
        Group: 'Gold',
        email: 'sammie@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Lennie Mike',
        number: '0803220918',
        Group: 'Gold',
        email: 'lenie@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Sammie sam',
        number: '0803220918',
        Group: 'Gold',
        email: 'sammie@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Lennie Mike',
        number: '0803220918',
        Group: 'Gold',
        email: 'lenie@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Sammie sam',
        number: '0803220918',
        Group: 'Gold',
        email: 'sammie@mail.com',
        tele: true,
        msn: false
      }, {
        name: 'Neville Lontus',
        number: '0803223111',
        Group: 'Gold',
        email: 'nevulle@mail.com',
        tele: true,
        msn: false
      }]
    }
  },
  methods: {
    createContact () {
      this.$validator.validateAll().then((result) => {
        if (result) {
          this.contacts.push({ name: this.name, number: this.number, email: this.email, msn: this.msn, Group: this.Group })
          sweetalert('Success!', 'contact created!', 'success')
        }
      })
    },
    deleteContact: function (contact) {
      this.$emit('delete-contact', contact)
    }
  }
}
</script>
<style>
.page-title p{
    font-size:14px;
    color:#959595;
    margin-top: 25px
  }
  .sort select{
    border:1px solid #ccc;
    border-radius:5px;
    padding: 10px
  }
.contact-inner{
  margin-left: 20px
}  
.contact input{
  width: 100%;
  padding-left: 20px;
  height:35px;
  margin-bottom: 15px;
  border: 0;
  border-bottom: 1px solid #ccc
}
.contact-input select{
  border:0;
  float: left;
  padding: 12px;
  width: 45%;
  margin-bottom: 20px
}
.contact-input textarea{
  width: 100%
}
.contact-submit button{
  border:0;
  color:#fff;
  background-color: #F2994A;
  border-radius:5px;
  padding:12px;
  padding-left: 20px;
  padding-right: 20px;
  float: right;
}

.draft button{
  border:0;
  color:#fff;
  padding:12px;
  border-radius:5px;
  float: right;
  margin-right: 12px;
  padding-left: 20px;
  padding-right: 20px;
}
.schedule button{
  border: 0;
  float: left;
  padding:12px;
  padding-left: 20px;
  padding-right: 20px;
  background-color: #fff;
  color:#959595
}
.closebtn{
  font-size: 15px;
  margin-right: 30px
}
.add {
  position: fixed;
  bottom:30px;
  right: 30px;
}
.wrap-plus{
  font-size: 25px;
  color:#fff;
  width:60px;
  height:60px; 
  text-align: center;
  box-shadow:3px 3px 3px #959595;
  background-color: #F2994A;
  border-radius: 50%;
  line-height: 60px
}
.secondary-btn{
 width:40px;
 height:40px;
 line-height: 40px;
 margin-bottom: 10px;
 text-align: center;
 display:none;
 color:#F2994A;
 border-radius:50%;
 box-shadow:3px 3px 3px #959595;
 background-color: #fff;
 margin-left: 10px  
}
.add:hover .secondary-btn{
  display: block
}
@media (max-width: 767px) {
    .contact-submit button{
    padding:5px;
    padding-left: 10px;
    padding-right: 10px;
  }

  .draft button{
    padding:5px;
    padding-left: 10px;
    padding-right: 10px;
  }
  .schedule button{
    font-size: 12px;
    padding:0px;
    width: 30%;
    padding-left: 0px;
    padding-right:0px;
  }
}
</style>