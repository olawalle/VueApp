<template>
    <Li class="col-xs-12 listwrap">
        <div  v-show="!isEditing" class="" >
            <div class="">
                <div class="">
                    <div class="col-md-12 contact">
                        <div class="col-md-12 name">
                            <div class="edit-btn pull-right"><a href="#" title="send notification" data-toggle="modal" data-target="#myTrdModal"><i class="fa fa-envelope"></i></a><a href="#" title="Edit contact" v-on:click="showForm"><i class="fa fa-pencil"></i></a> <a href="#" title="Delte contact" v-on:click="deleteContact"><i class="fa fa-trash"></i></a> </div>
                            <div class="col-md-2"><b>{{contact.name}}</b></div> 
                            <div class=""> 
                                <div class="col-md-3"><b>Phone number:</b> {{contact.number}} </div>
                                <div class="col-md-3"> <b>Email:</b> {{contact.email}} </div>
                                <div class="col-md-2"> <b>Group:</b> {{contact.Group}} </div>
                                <div class="col-md-2"> <b> messanger:</b> {{contact.msn}}</div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            
        </div>
        <div class="clearfix"></div>
        <div class="wrap" v-show="isEditing">
            <div class="form edit">
                <div class="col-md-6">
                    <label>Name</label>
                    <input type='text' v-model="contact.name" ><br>
                    <label>Number</label>
                    <input type='text' v-model="contact.number" ><br>
                </div>
                <div class="col-md-6">
                    <label>Email</label>
                    <input type='text' v-model="contact.email" ><br>
                    <label>Group</label>
                    <p class="contact-input">
                    <select v-model="contact.Group">
                      <option disabled value="">Group</option>
                      <option>Gold</option>
                      <option>Diamond</option>
                      <option>Platinum</option>
                    </select>
                  </p>
                    <button class="btn-success pull-right" v-on:click="hideForm()">
                        Save
                    </button>
                </div>
            </div>
        </div> 
    </li>
</template>
<script type="text/javascript">
  import sweetalert from 'sweetalert'
  export default {
    props: ['contact'],
    data () {
      return {
        isEditing: false
      }
    },
    methods: {
      showForm () {
        this.isEditing = true
      },
      hideForm () {
        this.isEditing = false
        sweetalert('Success!', 'contact updated!', 'success')
      },
      deleteContact (contact) {
        this.$emit('delete-contact', contact)
      }
    }
  }
</script>
<style>
.listwrap{
    padding: 0;
    margin: 0
}
.wrap{
    height:100%;
    margin-top: 5px;
    padding-top: 12px;
    padding-bottom: 20px;
    /* background-color: #d5d5d5 */
}
.edit input{
    height:35px ;
    border:0;
    border-bottom: 1px solid #ccc;
    width: 100%
}
.edit button{
    padding: 12px;
    padding-left: 15px;
    padding-right: 15px;
    border-radius: 5px;
    margin-top: 10px;
    margin-bottom: 40px;
    border:0
}
.sort select{
    border:1px solid #ccc;
    border-radius:5px;
    padding: 10px
  }
  .contacts{
    margin-top: 60px
  }
  .contact{
    padding: 10px;
    background-color: #fff;
    border-radius:5px;
    border-bottom: 1px solid #e8e6e6;
  }
  .contact:hover{
    padding: 0
  }
  .contact:hover .name{
    padding: 10px;
  }
  .name:hover{
    background-color: #e8e8e8;
    transition: linear 0.1s all
  }
  .name i{
    margin-right: 10px;
    color:#3f3e3e
  }
  .edit-btn{
    display: none
  }
   .name:hover .edit-btn{
    display:block
  }
  .details{
    margin: 0;
    margin-left: -15px;
    margin-top: 5px;
    color:#707070;
    padding: 0
  }
  .sec{
    width: 40px;
    height: 40px;
    line-height: 40px;
    border-radius: 200%;
    color: #F2994A;
    text-align: center;
    font-size: 13px;
    margin-left: 6px;
    margin-bottom: 10px;
    box-shadow: 3px 3px 3px #9d9d9d
  }
  .secbtns{
      display: none;
  }
@media (max-width:767px){
    .edit{
        height: auto;
    }
    .edit-btn{
    display: block
  }
}
</style>