<template>
    <transition name="el-zoom-in-top">
        <div class="content-wrapper dashboard-wrapper">
            <!-- Main content -->
            <section class="content">
                <!--end of New User-->
                <div class="row">
                    <div class="col-md-12">
                        <div class="">
                            <div class="row">
                                <div class="col-md-12"> 
                                    <div class="col-md-12 top-sect">
                                        <div class="pull-left page-title"><p><b> Contacts</b></p> </div>
                                            <div class="pull-right sort">
                                                <select name="sort" id="">
                                                    <option value="Sort by">Sort by <i class="fa fa-caret"></i> </option>
                                                    <option value="Alpabetically">Alpabetically</option>
                                                    <option value="Groups">Groups</option>
                                                </select>
                                            </div>
                                        </div>                                      
                                        <ul class="list-group" id="contact-list" >
                                            <contactform v-on:delete-contact="deleteContact" v-for="contact in contacts" :contact.sync="contact"></contactform>        
                                         </ul>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
            </section>
            <!-- /.content -->
        </div>
    </transition>
</template>

<script type = "text/javascript" >
import sweetalert from 'sweetalert'
import Contactform from './contactform'
export default {
  props: ['contacts'],
  components: {
    Contactform
  },
  methods: {
    deleteContact: function (contact, index) {
      sweetalert({
        title: 'Are you sure?',
        text: 'This contact will be permanently deleted!',
        type: 'warning',
        showCancelButton: true,
        confirmButtonColor: '#DD6B55',
        confirmButtonText: 'Yes, delete it!',
        closeOnConfirm: false
      },
      () => {
        this.contacts.splice(index, 1)
        sweetalert('Deleted!', 'Your contact has been deleted.', 'success')
      })
    }
  }
}
</script>
<style>
.top-sect{
    padding-left: 15px;
    padding-right: 15px
}
  #contact-list{
      list-style: none;
      padding: 0;
      margin: 0;
      margin-top: 70px
  }
</style>