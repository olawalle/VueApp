<template>
    <transition name="el-zoom-in-top">
        <div class="content-wrapper dashboard-wrapper">
            <!-- Main content -->
            <section class="content">
                <div class="row">
                    <div class="col-md-12">
                        <div class="col-md-12 top-sect">
                            <div class="container pull-left page-title">
                                <p><b> Notifications</b></p> 
                            </div>
                        </div>
                    </div> 
                </div>
                <div class="row">
                    <div class="col-md-12">
                        <div class="col-md-12 top-sect">
                            <div class="container">
                                <ul class="nav nav-tabs">
                                    <li class="active"><a data-toggle="tab" href="#in"><b>Incoming</b></a></li>
                                    <li><a data-toggle="tab" href="#out"><b>Outgoing</b></a></li>
                                </ul> 
                            </div>
                        </div>
                    </div> 
                </div>    
                    <div class="tab-content">
                        <div id="in" class="tab-pane fade in active">
                            <div class="row">    
                                <div class="col-md-12 container" id="accordion">
                                    <div class="col-md-12">
                                        <div class="">
                                            <h4 class="notification-title">
                                                <a data-toggle="collapse" data-parent="#accordion" href="#collapse1">
                                                <i class="fa fa-envelope"></i>  
                                                    today at 12:23pm  |  
                                                    Push notification sent to Platinum group members.
                                                </a>
                                            </h4>
                                        </div>
                                        <div id="collapse1" class="panel-collapse collapse in notification-collapse">
                                            <div class="panel-body">
                                                <div class="col-xs-12">
                                                    <div class="col-xs-4 bor-right">
                                                        sent: <br>
                                                        priority:
                                                    </div>
                                                    <div class="col-xs-8">
                                                        Lorem, ipsum dolor sit amet consectetur adipisicing elit.
                                                        Aperiam minima, voluptates saepe perspiciatis,
                                                        amet inventore magnam, iure veniam architecto quam molestias
                                                        tenetur vel mollitia recusandae? Incidunt ipsum rem non blanditiis.
                                                        <div class="col-xs-12">
                                                            Delivery Status <br>
                                                            <span class="status">
                                                                Delivered:
                                                            </span>
                                                            <span class="status">
                                                                Pending:
                                                            </span>
                                                            <span class="status">
                                                                Not Sent:
                                                            </span>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                        <div class="">
                                            <h4 class="notification-title">
                                                <a data-toggle="collapse" data-parent="#accordion" href="#collapse2">
                                                <i class="fa fa-envelope"></i>  
                                                    today at 12:23pm  |  
                                                    Push notification sent to Platinum group members.
                                                </a>
                                            </h4>
                                        </div>
                                        <div id="collapse2" class="panel-collapse collapse in notification-collapse">
                                            <div class="panel-body">
                                                <div class="col-xs-12">
                                                    <div class="col-xs-4 bor-right">
                                                        sent: <br>
                                                        priority:
                                                    </div>
                                                    <div class="col-xs-8">
                                                        Lorem, ipsum dolor sit amet consectetur adipisicing elit.
                                                        Aperiam minima, voluptates saepe perspiciatis,
                                                        amet inventore magnam, iure veniam architecto quam molestias
                                                        tenetur vel mollitia recusandae? Incidunt ipsum rem non blanditiis.
                                                        <div class="col-xs-12">
                                                            Delivery Status <br>
                                                            <span class="status">
                                                                Delivered:
                                                            </span>
                                                            <span class="status">
                                                                Pending:
                                                            </span>
                                                            <span class="status">
                                                                Not Sent:
                                                            </span>
                                                        </div>
                                                    </div>
                                                </div>
                                            </div>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <div id="out" class="tab-pane fade">
                            Lorem ipsum, dolor sit amet consectetur adipisicing elit. Provident iste iure nostrum 
                            nemo suscipit quae animi non vel, inventore voluptas
                            cumque aut! Delectus recusandae facere voluptates porro ipsam pariatur iste.
                        </div>
                    </div>
                <modal></modal>
                <!-- MODAL -->       
                <div class="modal fade" id="myModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel">
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
                <br>
                <br>
                <br>
            </section>
            <!-- /.content -->
             <div class="add pull-right">
                <a href="#" title="enter details" data-toggle="modal" data-target="#myModal">
                    <div class="wrap-plus" title="Compose new Notification"><i class="fa fa-envelope"></i></div>
                </a>  
            </div>
        </div>
    </transition>
</template>

<script>
  export default {
    name: 'Chat'
  }
</script>
<style>
.content-wrapper{
    padding-top: 50px;
    padding-bottom: 50px
}

.notif{
    padding: 20px
}
.notif-btn{
    border: 0;
    padding: 8px;
    border-radius: 5px;
    padding-left: 12px;
    padding-right: 12px
}
.tab-content{
    margin-top: 12px
}
.nav-tabs li{
    width: 50%;
    text-align: center;
    border-bottom: 0;
    font-size: 16px
}
.text-center{
    color: #17286a;
    font-size: 16px;
}
.accordion{
    padding-left: 30px
}
.notification-title{
    background-color: #ffff;
    box-shadow: 3px 3px 3px #dbdbdb;
    width: 100%;
    padding: 15px
  }
  .notification-title{
    font-size: 14px
  }
  .notification-title a{
    color: #575757;
    text-decoration: none
  }
  .notification-title a:hover{
    text-decoration: none
  }
  .notification-collapse{
    box-shadow: 3px 3px 3px #dbdbdb;
    padding: 15px;
    margin-top: -7px
  }
.float-btn{
    height: 60px; 
    width: 60px;
    line-height: 60px;
    text-align: center;
    box-shadow:3px 3px 3px #959595;
    background-color: #F2994A;
    border-radius: 50%
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
@media (max-width: 767px){
    .nav-tabs li{
    width: 50%;
    font-size: 10px
}
} 
</style>
