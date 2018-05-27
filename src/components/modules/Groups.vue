<template>
    <transition name="el-zoom-in-top">
        <div class="content-wrapper dashboard-wrapper">
            <!-- Main content -->
            <section class="content">
                <div class="row">
                    <div class="col-md-12">
                        <div class="col-md-12 top-sect">
                                <div class="container pull-left page-title">
                                <p><b> Groups</b></p> 
                            </div>
                        </div>
                        <div class="">
                            <div class="row">
                                <div class="col-md-12">
                                            <!-- <button v-on:click="showForm" class="btn-primary pull-right my-btn">
                                                <i class="fa fa-pencil"></i><span>Edit</span>
                                            </button> -->
                                        <div class="container-chat clearfix col-md-12">
                                            <ul class="Groups-list">
                                              <li v-for="list in lists">
                                                <div class="col-md-6 groupcard">
                                                    <div class="box" v-show="!isEditing">
                                                        <div class="">
                                                            <div class="events-nest ">
                                                                <div class="wrap-no-pad">
                                                                    <div class="row">
                                                                        <div class="col-md-12">
                                                                            <h3 class="Groupname">{{list.name}}<div class="pull-right els">
                                                                                <div class="dropdown">
                                                                                    <button class="btn dropdown-toggle" type="button" data-toggle="dropdown"><i class="fa fa-ellipsis-v"></i>
                                                                                    </button>
                                                                                    <ul class="dropdown-menu">
                                                                                    <li><a href="#" data-toggle="modal" data-target="#notificationModal">Send notification</a></li>
                                                                                    <li><a href="#" @click="showForm">Edit Group</a></li>
                                                                                    <li><a href="#">Delete Group</a></li>
                                                                                    </ul>
                                                                                </div>
                                                                            </div>
                                                                            </h3>
                                                                            
                                                                        </div>
                                                                        <div class="col-xs-4 group bor-right">
                                                                            <div class="">
                                                                                <img :src="list.url" width="90%">
                                                                            </div>
                                                                        </div>
                                                                        <div class="col-xs-8 ">
                                                                            <div class="description">
                                                                            <h4>
                                                                                {{list.description}} 
                                                                                <p>members: 2000</p>
                                                                            </h4>                                                       
                                                                            </div>
                                                                        </div>
                                                                    </div>
                                                                </div>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </div>
                                                    <div class="wrap" v-show="isEditing">
                                                        <div class='form edit'>
                                                            <div class="col-md-12">
                                                                <label>Name</label>
                                                                <input type='text' v-model="list.name" ><br>
                                                                <label>Number</label>
                                                                <input type='text' v-model="list.description" ><br>
                                                            </div>
                                                            <div class='send'>
                                                                <button class="btn-success float-right" v-on:click="hideForm()">
                                                                    Save
                                                                </button>
                                                            </div>
                                                        </div>
                                                    </div>
                                                </li>
                                            </ul>
                                        </div>
                                         <div class="add pull-right">
                                            <span class="secondary-btn" a href="#" title="enter details" data-toggle="modal" data-target="#myModal2"><i class="fa fa-pencil"></i></span>
                                            <span class="secondary-btn" a href="#" title="Upload from file" data-toggle="modal" data-target="#myModal2"><i class="fa fa-upload"></i></span>
                                                <a href="#">
                                                <div class="wrap-plus" title="Create new Group">+</div>
                                                </a>  
                                        </div>
                                    <modal></modal>
                                    <!-- MODAL --> 
                                        <div class="modal fade" id="myModal2" tabindex="-1" role="dialog" aria-labelledby="myModalLabel">
                                            <div class="modal-dialog" role="document">
                                                <div class="modal-content"> <a href="#"><h2 class="pull-right closebtn text-danger" data-dismiss="modal"><i class="fa fa-close"></i></h2></a>
                                                    <form  @submit.prevent="validateBeforeSubmit" class="contact">
                                                        <h2 class="text-center"><b>Add Group</b></h2>
                                                        <fieldset class="contact-inner">
                                                        <p class="contact-input">
                                                            <input type="text" v-validate="'required'" name="name" v-model="name" placeholder="Group Name" >
                                                            <div class="form-error" v-if="errors.has('name')">
                                                                {{ errors.first('name') }}
                                                            </div>
                                                        </p>
                                                        <p class="contact-input">
                                                            <input type="text" v-validate="'required'" name="description" v-model="description" placeholder="Group description">
                                                            <div class="form-error" v-if="errors.has('description')">
                                                                {{ errors.first('description') }}
                                                            </div>
                                                        </p>
                                                        <p class="contact-submit">
                                                            <button type="submit" :disabled="errors.any()" data-dismiss="modal" v-on:click="create" value="Create Group"></button>
                                                        </p>
                                                        </fieldset>
                                                    </form>
                                                </div>
                                            </div>
                                        </div> 
                                        <div class="modal fade" id="notificationModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel">
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

<script>
  import sweetalert from 'sweetalert'
  export default {
    data () {
      return {
        isEditing: false,
        name: '',
        url: 'http://thenerderypublic.com/wp-content/uploads/2014/03/social.jpg',
        description: '',
        lists: [{
          name: 'Gold',
          description: 'Compilation of customers wit a gold customer status',
          url: 'data:image/jpeg;base64,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'
        }, {
          name: 'Platinum',
          description: 'Compilation of customers wit a platinum customer status',
          url: 'data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxMSEhUSEhMWFhUXFhgVFhcXGBcVFxcYIBkYFxYWFx0fHighGxslGxcXIjEhJSkrLi4uGB8zODMsOCgtLisBCgoKDQ0NFQ8PFS0dFx0tKy0rKy0tKystLS0tNysrLS0rLS0rListKzcrLS0rLTctLSsrLSsrLSstLSsrKysrLf/AABEIAOEA4QMBIgACEQEDEQH/xAAcAAACAwEBAQEAAAAAAAAAAAAABQMEBgcCAQj/xABHEAACAQMCBAMGAgUJBgYDAAABAgMABBESIQUGEzEiQVEHFCMyYXGBkUJSYqHwJDNTcoKSorHBFWNzk6PSNEODtMLhFhdE/8QAFQEBAQAAAAAAAAAAAAAAAAAAAAH/xAAUEQEAAAAAAAAAAAAAAAAAAAAA/9oADAMBAAIRAxEAPwDuNFFFAUUUUBRRRQFFFFAUUVG0wH1PoNzQSUUr4px63tx8eeKHPYSOoY/Zc5NZPintZ4ZD/wCe8p9I4yP3vpB/A0HQK+ZrlY9rBf8AmOGXUvoR1CD/AHUaj/8APOJsPBwaQZ7alk/eCq0HVM19rk5584ooy/B5D66Ul/01GvkntYaMZm4bcQ47lzIg/wAUYoOs0VznhXtasJQNUjxnz1BWX9xz+6tfw7j8E+OjNFLnyVxq/unegb0VEs47HY+h2qWgKKKKAooooCiiigKKKKAooooCiiigKKKKAoor4zY3NB9qKSYDP03PkAPUnyFZ7mznC3sYupO+M/Ig+eT+qPJfVjt+6sQLHifGsG4LWVkd1hT+ekHcFs9h9X+hC+dA+5h9ptrA/Ri13U5OFigBIJ9NWCT/AGQaSe78e4j88icPhPZE3lx9lOfuGdftWt4VwKx4YqrHGEZ9sgapZMbnU53bv2zjvgbVdl4tqMQiIAd1KspDiSI9mU433aMnHYH0wSGV4b7JrJCGunkuHJyTLIVDHz8KkZ+zFq1fDeC2VsD0LeNMMFbpxqhz2yTgZA9c+VQceEAuAbptMbxaEJYqNYLE6SMaZANxjc5JHyEivb8dLQiSOCSVXA0tGA3UZG07Y2AOklXJCMCDqA3oHvvi/qfpaWGQSuwYeu+DnHp+Gan+2GA3t3XPyHAKt4wmMjODvkBsasjGdyKXuVyzGRY1Ryy6tUmFYFQrONKt4kGQAww2TnshHv3K+bCN0NCAkEM56pzlQyaPhDO+QzkYA33NA5spC5YMiDZTswLb5zqHl2G+Tnf03rvxKMSGMo2xA1YOknfYHsezfXwnbtmvwexniD5ito/AFTpliWYZ09Q9NfCM+QPc0qvrS+1FhH6O4imUjI0NiHWgOsMpGG0owLEnLbBcuuE8OvF1SQwv9XRS2+cYbGdwCcg9t+29ZniXsgtW8dpLLbt3XS5kTPcEhjqP4MKu3PEioJuY8Kx0qksRHVw2AyAFyZApUCMjU2gMMdg5v7ho0iHxlI+JIIUM0i6iXwVAYsAMqQAd3UjGxEGHlHHuHfq30I8hl3x6lG8efohanHLntOtZ20Pqt5QcFJMlQR3B21KfuCB61rLfiDKAJCr5k0KQChO5J2yd1AO2d9JOd8BfzDylZcRXMiAv2WRfBIvoVbGSPocr9Ko0FveqwByMHcEEFWHqpGxq1XGrqy4nwUl0b3q07uNPjQfrOmd8DHjTHbJwK3PKXN0N5GHhbO2WQnLL9V/WX8iPMUGsorxFIGGQc17oCiiigKKKKAooooCiiigKKK8uwAyaD5LIFBJOAKwvO3Opt2W3t0615JtFCNwPR5MY9CcZGwySO4j555vaJkt7ZDJdykCCMbjcfzsg7YG5wdhjUcAV65P5VWySS4mYzXLqXuJ8FmP6TJGO4TP4sQCfIAK/K/JBEpvuIOLi7OG1HeKHHYRjGMj9bG2PCBuS7HGeujm2I6S/NKrgtjsRgbqQCHI7hQPNsCf3mUSB1Jbv0okOEdSG0s7Y3yMMT5HAGwJexcRiR+tayRiRfhPkFlYY1BXAIOQH1KfRz5PmgT2/ExFKNb50sViE3w5JGLNGUjYqiSHUcAJn5++wL3bO1kuFnUrJboxHSK6BIDl2kkUEMBnWF8Qzs22MGm1jw5I9WnVhn14ZmYKcBcJk+FQFAwMDv6mk3MHPFtakRLmadvliiGt29CAPL6nA2IzQacxgjDb/AHqC54hDECXkVcd9xt96wiw8Yvz42WxhPkAJZiM9iM6FyPI6iPWr9n7M7PIa46l0487h2kx9l2UfbFBau/aRw2M494V/+H8Q/kuT+6qg9p1ofljuG+0E3/ZWns+B28QxHEiD0VVX/IVb91T0FBj/AP8AZtoPmS4X728//ZV219ofDnOPeUQnyk+GfybBrRG0T0qnd8Bt5Rh4kYfVQaC3bXkcgBR1YHtgg5oFlH1GlCKJGUIXAGsqCSFJ9ASTj61kLn2b2wJa2aS2c/pQuyZ/rAHB/Gq5bi9j5rexDuCBHMB9MeFsDyABPrQM7nhFxHpYn3gJhEVFETqCrK7udelt9B8IBCq2AxODFYStctrjzoPwkeKVdUWBmSSSNhgMH8Ok6yCBshLCrnL3OttdHp5MUwHihl8DjGM7eYGe4yPrTabhMRZ5VRUmeMxmVVAfB7b9zggH8BQRNxOMP0WDkqFBcqcegJYDA3B9PlO1Yjm72eMrm94Y3RuAdTIDpilP4bI/owwDvnGS1NVLRydO4jSIt4gQxdHaPB6gJA0lVUEZwwCeiZLexvDEAXVgsrqkUYA14zgyuNiNRYZH6I0khfEFDMck87+8MYJ1MN2h0vGw062+3YP+5vLBOK6DbzhxkVi/aDyKt4ongIjuox8OTyYf0cuO6H17r5ZGQVvIXNTvqt7gFLqI6JEb5mx6/rNpGQwzrUeo3DpdFRwTBwCOxqSgKKKKAooooCiiigKyXPPM6WcLSMckHSqDvJJ3VBj8z+XnWh4nddNCfM7D7/X6VzPgUQ4leG+cFre2Yx2oYbSSggvOB5hT2PrjsUoGXI/L0kWu7vPFeXG8hO/RQ7iFfQ9tWPMAdlGWL8RaXpuEliQ/JKCpQ6gABIMllJyuG0kKw3JBIa1HxZHCtbusuGHUCjWyqV1KyrkFgS0e4zkOCAQQahls5HjItpkjhkzrjkiMunPcIQ6EKRuAwJww7ABQHm2WSYFVkBQt4m0GORCVzmPIaNyxIbV8vng51FvaxQ2kO2ERcsSSSSTlmZid2YnJJOSdzXiAJBCNbnTGgGpiCzYGMnsMn8B9hWRsbOXjMnVl1Jw9T4EGQbkg9/IiHP4vjJwAoUJG4necWYx2WYLQHD3JGS/qsIPzH9o+EZOM4DHWcucp21kp6SZdt3lc65ZD5s7Hck/lTi2gWNQiKFVRhVAwAPIAVLQFFFFAUUUUBRRXyg+0Giigz/MfKVveDxrpcYKyL4XUjcEEbgg1nYeLXfC2Ed5me2JwtwB4k9BIB5ftD8c5LDoVRXNusilHUMpGCCMgigpXEEF9BgkPG2GVlbBBGGR0ZTlWBwwYH0INZq4triB1Eki9NAUjnLB5pPCWOIhEER1AlwwJGkkaD2FC7s5uDS9aDVJYscyRbsYSTuyDvoydwNwTkAnIfYzRwX9uMHUjhXRlI1KwwySIwzhgdLBh9DuKBXwbiDKdlzGWCsnaWInPim1HzwRgdtOBqBXCX2jcqNMEvrP/AMTEARpOOvGPF0sj9LsyN5ED6Fft7FPGyRXCx3LN8NIE0hrhVIHWlLaVB0amKY0DQRqPgxr+BW8iw4nADEsdAbXpUnZS2BqbzJ7ZY4yADQZnkPmpLqJZFPfAkXtpb1x5A4O3kc+RXO4BrkfNVkeFX/vqKfdbltFwo2CSntJ9A+M58nUH0FdI4FfdRAM52BB/WUgFW/EEGga0UUUBRRRQFBoqlxe76UTv6AkD1PkPxO1BgfaNxaSTFnbn4tw/uyHvpBAM0n2VMj6YatFwvh8dvFHbxjEcahF9ceZPqxOST5kms1yxGbi9muDutsPdIj6ytiS4f7+JQD6O1MOE8za5wunMTlxG2FKvpVXCqQSzSNEeqoGBoYDcq1B44XYrPCi9RkljWEBgzaQw8adRRp1KTrGzeLXg/Rjy9PlZt9Xxj4iQdQ6cekk9t00H7k0t4LaxzRhSXDRog1xyOhJPUhlGpT4lJgBwcjse+9eOY7gWlutvaoOpK3TiQ5bVI5O7kkltTFmYsSSFkOc0FedDxa6NupIs4CPeCNuo2AVgH3BBbzC4XYs4rokCqoCKAAoAAGAABsABSjl/hSWVskCksRku53aSQ7ySMfMsxJ3q+slBeU16zVQTVKslBPRUPUr51KCajNQ9SjXQTZozUeqvuaD3RmvOaKD3RXnNeqCOaIOpVgCCCCDuCD3BrAWzNwm7ERybOdvATv03J+T8SdvMk4wS2V6HSvmPhC3cDwt5jwn9VvI/x5ZFBf6SMVkwpIB0tgE4OM4PocD91YufjapJ7zPOqJlnhjwFMg04XMhJwoWQfDUZLb76gtW/Z7xhpImt5v56ElGB7+E6Sfz9MDJIGy0ktOKQ2krRSxSLcqOkipHK7TxjBjEOF6Z1MAdRIKZIONOqg0t7CnEbWaCeMrlSjodJZdzhhgkalZcjc7qDWN9n/F5Iy9rcH41s5iff5lzs489J1KwPn1T5LW05OLsk0rgDqSKVwdWxijZ98DI6rS4/Z01lebLAW/EYrnGEnUwSY761VmRvqzQ9Vf8A00oOlI2RmvVK+A3BaPB+ZSVP3GxppQFFFFAVlueOJLFHlvlRXnb7RrqH+PRWprmntBHXc2/cSvbWx+iyS65fP+jiz+FB94faSW/C4YhqE1wVVyPmV5iZJiD+sqlwv1VBTKCK1aD3aZVdcFyjKskbEZdtCklsDcLkDYADyphzCkBtnW5HwjjIGrVq1Ax9PT4upr06dO+cAb1kOC8CjYysZGjimaN21SSTTMgj8MZkDNpU62ZnBPz4UjTroHXJVrphdwqojO3SVflCBmYhdgNAkeVVxsVVSNmqtwNBc8QlujvHar0ovMdWRQzMPtCU+xmf1p9xq4WK2YjCqE0jTgBV+UFcbaVG/pgUq5RjMVjEzDDzBrmQftzEy4/BWVf7IoH8k+9Cy0s9486lWX+P4/jegZdSpkkxSyOWpxJQW2moEtUy1fVagvg17Q1BCanoJFNes1AXoD0FgNXsGq4epFaglr0DUeqvYNB6or5X2gwnMcZtOIRXSjwS4R/qw2G36TMp0qOwyxrV8XkxBJIvcRuyn1IUlf8ASl/PFn1LRyDgx/EDDcrj5iPrpLfnXzgc4ns1BGPAY2A30gr4V+4Rl/GgytjcXUrG2jikibqSN13jV4FhQssQQkkMzhIUKYDKFc7bU343quuHs6g9aMCRFz4urHpnhUn9ZgEB/rmq/DuYXhgw0ZeSKVo51jXXIHZgwdVLAsjF9SqMsVkjAy2QbXLPF0uDcNDkxhkYOY3jBkPU1qA6qTpRYgTjzA3INB95Pv1YjSfC6qy+YIwNJ/FNDf2q2Ncz5bBhkWPGlY5JIVH7KSOif9GOA/2q6Wp2oPtFFFB8Y7VziZOpxCDJ/wD6J5sfSO3WAf4566LN8p+1c74R4r+M+kd/+B96tR/lQLuaeJw/7S6NyXZUjQwwhSVkLBuqBjPjOVBz3QOo2ZqrTe5PEDbxMzq8HSjeWVzE2vUsMcbNiFiy9PYeEsSQFXe5zLZNJxSF4JIEniV2AmLjUpATbQQxO5G2djvU9lcSW0ji6HWvGfwYxGjKVHih6hGrAOlsnUAuNh3CTneEx2CWurLmNLfIGNRbRbEgemZQceWBTnisoHhXYDYD6DYfuFZzjks0ktqlwEWTr2rHpsXTS12HXBOMnRCuSNs9tqv8Wm8VB9EtSxzUpSerEc1A5jmqyk1J45qsLNQNA9TJS2CSrkb0DBGr2Wqis/1qZZM0EmqvYNRBqlUigkBr2GqNa8u+KC0r1IGqkklSq9BbVq9Zqur1KrUHy5iDqynsQQfx2rG8guVSWFtyhUsfWQl9f5BY/wAMVtc1heAt07q5TYAvO5JIAGmSMDJ8tmP5UFHjvE7I3TablIbkIUYO4QSJuVznwq651xvnID5xpatXwnicN1D1YXRh2JQ5U7lcr+zkH8jWXLm3aaF0Egd+tbghGEoOCU8RALqNKAZHgjjwRkmrnAhdCfVNDFGGR2Yqw1MNliUoo06wvT1upK+BQNiKCjeDp3Mp9Zo5B9NcNvH/AJ20h/E10O0bKKfpXPOOgi6k9DFaH8Q/EM//AB/dW+4Wcxr9qC3RRRQeJ/lP2rn3Aj/LFHmFvx9v5TZv/k9dCkGx+1YSyt9F3qJ3Mk6KP68cEp/9o5x9DQZa7uOtcXs2ZIZIZJIFljZZAqL2E8eglEZskMCCfIjFN7TiwaOOG6t5RbS5QddWUo6qH7t4t01OpGTmNt9RGnD88XU9hxmS4tQxMgVmQZ8YKDUu31BOfI7+tbOWW7vbMC1KusqiSNpHIZFz4GKsrEspAzhsFhvsRkKNzbe73SxBmZY7q0wXbW2HumJyfo0376Y8abxVluLcRYzTuwwUj6+PPVC8U4H/AET+BrU80phyR2ycfx9qBYstTRz0qEv1qRJ6B1HPVyOWkEc1XIbj+P4+9A+ikqcT0minqbqmgZib61Pb3Oe9JuvXuOeg0IlqaOakkVxtVmKf60DlZajnlzVRJaimnoLqyVKsv1pWJ6kSSgapJVlJKVxyVOslAyRs1zuRl692zo0kem5Ro0DFmBkhzp0+LOAdxkjuNxW+tnzWI5XfqT3DjszBgfqzyBgP+Wp/EUFBJWMAS9jVbIZz74Ve4lA3UhAAEOT8zsH1Hfc73+UYLHXK9m7OVVEYtJLKEUliIlMhOk5TLJ3Hgz3FLRFeXR95guIkBI0Eq0hjCqreABTkmQywnONIUkZcsDf4Vxyb3lLed4y0kZkEcbdTpxqMdR5MDWWbQAQoHiYHUVyA+cyv/KMf7qHP2L3YH781vOE/zS/aue8fXN4d/wDy7ZMfVZJ5D+6Va6Nw9cRr9qCxRRRQfDWD4q+i+RT2zHIn0OpoJT/yrlj9lNb2sXzvbASQyHIXWYnI7hJVMJI+xdW/s0GM5mMicdDxlg5sdcahtAdwzJpY4O2AT28hS4e0CFbi3MClS8pEymNotDucMWX5dRkOTpzsZcEFhhr7UdS+4cRKkaHMNwo/RWUeJT9FYOv3qgzQi6nWaCFheTDpMFBlEnREvUjbVgAy4AGNz3ODQeebbyOPiCuR8OQRucgZ6brokGPXDOD9sU5fMljCW3eNOg5Pm8JMLH7NoD/ZhWK54gmYRXQRmg+IgfHhGZpCurbsQ2x/g6DkLiXXheJtyy6x3/nY1SOUf2oeg/3jlNAueX/OhZtqr8VTRIR9aqdb6/xv/wDdA6jlqeOff6UmiuKtJN6UDqO57b1bW6pCktWEmoHHXqeKWk8c9WVloHMctTLNSlJtq9+8UDtLraonnyaTNdV9Wf0oGyzVcikpFFcetXYp6B3FNVhJKTxTVdtXyaBjf3ghtpZScaUJz9cYH7yKznJlsUgLMMF3ZiPTAEZx9CULf2q+8/3jCKG1j3klYNjvsCFTUP1S7Ln0AJ8qv3zC2tvAdIjRUU7ZVRhde/cquW376aDLcb4UiSS+5lzLI4YwtMy2gmYnVI0YG+NLsw3BKaApY+Fnyhy6LQSyPIZ7iU5mlOzMQPDGoONCgdgcdx2GMZK35T4mGaX3wW8U6iS6056kIC5McYIPiSPC6gVOwz9dTybdBILiZyVgikYLk6sRwwxxynUd28ccgye+nNBXiYzX8hGdPWwO2xjjjhddv20Y/ia6hCuFA+lcx9nFszsJHHjI1yefxXJllx9NbsPwrqNAUUUUBSfmixE0DKfQ04rzImQRQYCCBeI2U1vMAOqDqwMBJdREmPqs6mTPpMlcP5fWZL5FmlYC06hOssyxrHqDqgPYZ9K7mqm1vGXB0S5cf1gMSr+KAOB5tCo86537SbJbHiTXUsbPbXkTRydM4IbCiTSe2SFVhvuC3pQNbHm1jILWCMXNoqpDKAYmjjjc9OFDp7qNlLAnyzknfE8L4oLS+dInHTEqmF2woBGWhMnoCrNG/oskvpTjg3HpHCzRqkNpb6IRI6uJeljHTzllZQwU7nw9RgM5JpTwDgk0kM8q6IvelZENxq6awlgzE4ViWJ0KoAzszDGAaDX822okRLmIHQ4yA2NS4JVkf9pGDIR6qaxomx3rT8rcTVTJZ3M0Tju0iMXjB0hVnyQCq4AjlyBjTHIdtbFNzJwdoJGVgRg4x6GoKsdxjFXIbn+PKkXUI71Mk9UaJZqnSSkcNzVyKfJoG8UnlV2OSlELVcR6BgZajM9VWlqMy0Fzq16SelxmoE9A5jnq1HPSGOerUVxQaCGfNaLhCAAyOdKqCzE9gBuTWa4Nbs7DFR8+cbCgWEJXUTiUncFtiIjjOwypbY7lV/SJATcBmN5ey3rjEcY0x6tguxAO/YrGzZII3mdT8tO+LXYYRhMN8UB85wF6coycjddegE7jxCstJKi2MUdq2pZZGjDttqf3eaZJCSSd5VjfVknOcjOaXcI4FPYXHRtW61nI6odbAPGThZHQKcSJ4lBIxvnIGkkgj4f7RS0dwhEjXEkjLahUB1B3DQKxyD4WJ7g5DkeZI2nHbYWnDrewGMuFjfT5ovxLkjPkx8G/9OKz3sW5WQp79KuWDFIsj5SNmcftZyPpT65zeXxI3RPhJ6aVb4jj+tKCPqsKHzoNjyNYlItTd23P3Namq9jAEQKPSrFAUUUUBRRRQZ/mzhpkTWhw6eJW9GG4P51lOIcOTivD3tj4HG6DyjkQjMf9VSwA7fDkjI3Bx0mRcjBrn/HoGsp/eFz0mI6uAW04zpmCjuVBYEDdkZx3xQfnNbGVZvdHJjPU0Orv00DAlTqJ2GDkZIrqwh4ckUkclnF04sp8S6kLuVXqMqNrChwpzjwjvjavPtm5TE0Y4nbKDgAXATxArgFJgR8wCkeLzQo22DWVt+ZrORIEk94gMLxuFHTmh+GRpABXWNhtknu2c5JoPnGOH2sSC+4bJIqo69SCUZeEtspBI8SkHBU5yD3YZxqeXeNRX8IgmKq6DTG5OQvYCKQnfp9gjnt8jH5GebiNkOLxB/8AaMR041HpSvg4bQjtkFFBdsZQZJJx5Vz/AIvy7e8MdZJB4M4SaM9SJtvlzjbIJ8LgZBO3egb8f4Q9u5VwRg4wfL6UnLfx6Vr+X+b4LuMW96N9lRh86eXwyT4k8+kx1DcIzeFBX47yhJEvViIlh3xImcAg4KOO6OOxU4IINQZ2KWr8E1L9BHcfnU8W1UOoJavpLSWB6vRSUF4tVaaWvDyVUlloJjP6/h96+ieqDSV7hVicAZqBjFMe1PuC2LSkYFeeXeWXl8bABRuzN4VAHcsewG1WOY+dYLFDDaHVJjeQbMf+ECDpB/pGG4+RWzqFDbmHj8fDozFGw94OzMMHpZAOBnYykEYB2UHU3kGxvLFvxFybm0EUYJKmWdyocA50Rn5iMksWGdRyTuDnnt9xN5Wyx9dsnABOTjc+ZJJySTuSTkno1hM97BDPHcIGiQAwEEQkqhUo6qdSqAEK4BGSxxlqD1zIvEFttK28OUlWfXbyhlBTJyIzhu5YEAdiTWTk45qlhHCo5Ip5F6cq4VlZydulqLBVyXORpxqzVnibn3Zr6Jp4ZpI44pcwpDFMHXTLp2wzEhnyuwXHbFa72T8rpaQHid14WKfCBGdEZ21gdy75AUd9wBu1Bo5l/wBmcOhs0f4zIV1L3DHxTzDPoz4X9p487ZpzyBwQRoHKgbAAeQAGFUfQAAfhWf4RbPf3JmdSBkYU4OlRnTGCNjjJJOd2ZiNtOOo2sARQo8qCaiiigKKKKAooooCqvEbNZUKkVaooOZRzPw2XpyYNoxIye0WSSVb/AHRJJ3+Qkn5SwrmXtU5C90b3q2B90cnIA/mHJ+RvRSTsfI7fq6v0RxnhSToVYeVYSJ2sc21wvUtGGgahqCIRgxuMHVFjsdyvbDLsA5TyJcCG3klhh686sxkC4WaNMAAoc6mU9/CO+cjYZj5P49dS3MkcaxvDLqZ7WR41jKE7pH1CF1eLIXsTvjbZ7zj7PpbJhxDhTu0Q8elTrkhB3Hr1Iu+++3fIy1JbPmSykWaSVOjNLEUmVVLRTnuHjAGUk75yQDnJJOSQVcd5bkivfd4I2bqHMSYJbHcqc/qjJOey4JxvTyz41xHhTAXEUqqwCgtghgB8gfDI4Az4GDafIL3rxyxxaK5TqcQcM1rjRI+WJRgUGvA30tpIbc50j0NWeC3ge3ne6klaCWUoqOvwWQtojeM/osrBsgdh4huooHUPGeF3+0i+7ynzjAUZJ7mNmx3wBodif1R2ol5Gcn+TSxzbZ0htMoHq0bgOPyrOcD4KvQuoLh2WOG51MVIGR02wQTlVzpXxYOAx74wYrK0vpficPglFr2QM46bY2LIsrYbceWcHP2qBvJwG4jPjhkX7qw/0oW3b0NLx7QuI2jdKQsrJsyOJFK7DHgDqgyDn5dx61cPtYm/TQN91g/1gJ/fVExtmPkakg4FNJ8iMfsCaqP7WJh8sag+oW3/y93qvL7SeIz+GLW2BuIxLkfcRso/NaDUxckyLhrhkgUnAMjhM/QA7k/QCvdzxfhlhtvPIPIho1/u4Mh++kKf1hXPeG8Ra7keKe4kilbZCoVAzbgpKFUFj6An6VJPwFVuLOzZcPpLTtEd2BJPzHIHhU+LG2c4PykLXM/tFuLnwKdEY+VVAUDzyqDIU7dyXYeTCqPLHA47hXuryVkt0J1EEdSWTZmAJzpA1KWfBPjUAMzCtLw65JuHs2sIIoRF1QkkI6jLqVVZi2WOc+Z1gA+PIzVxeOQW00VjbFQwcRgkqeiF1NpZsaTO7kg6c4LsAewAVOX+d7dZhb2cMNpCc/EkGXffYF2OQdzuzEbdhnFL+duPXkTI6TQmKQMoEaRSDK4EgLlTr+ZcnbOflXtVbivA7W3lluL6XUXkd47SM/FKliU6zbaRgjIG538QIwWHLHLr8UZbm4VbXh0OVRVyqkFt44/NizYDP3J2AzsAk5G5fn4nJ77xGZ3tYctmV8K5G7qM7JGNILMMDAx643V/eSX0wiiBWFT4QRpOe3UYfotjZV7oCSfE2I4rm4e6ZbW2TpW0ZUKqjGdPYtjbY4wgyFIySWwI97y3wFLdBtv50FngPCVgjCgeVNaKKAooooCiiigKKKKAooooCqPEuGpMpVhV6ig5zLZ3PDmLQDXFkkxk4xnuYzvpJ8wQVPmM71m+YOSLHioaa0ZbW77vGRpjZvWRP0CT+muV3/SPbs00IYYIzWS45yerHqREo43VlJVgfUEbig/Ol3wu84RcfyiDTnK4YaopUPcBhsR2PqDjavsnMUDywZtmSCEnwCTqPjJYKGZRlQxzhsnyzXcpeIzRoYL63FzCdjlVO31Q+E/cFfxrLcV9mPD7wdTh9x0JO5ibMiDv3BxJH3G5BXbYUHOuB3PvF27s6pHnrdKZ8xuVxoVgcK2O+CMYXGCNqa838YlnW1KSEPLga1kkj1E6Rho2ACqCcKwJGB9qo8d9mfEbbxG3Mqf0kHxlP4L4gPqVFL25rvFXpBlQgaWIjjWRh5BzpztQbriHLQuTC95MUiij0ahjqSNk6vHIcImQDqbUck4B8RpXxs8Ms9KjhwmV1yshuZWyAcE5RwD5bhQN/vWFtrnEyyzAyjXlgxyWx6k5z5d9jWo4pLYXjCWS/mjIGkRta6wg3OAVl/M753oGB5UtruETWqvaswysbyLNGw3BxgmRBnzbPb5avXst3ZWUJ6ksCxFFmiRY0J8QDlTgqxOchxqznxZ2Azt/xO3S0e2Fy11sBDmExdPfJyWY+EADAGfTYUl4bx94lETok8OciKUagpPcxkEMhI9DjfODQbq/lF9NDBLAS0sOuOViqXMTjJAZhhXBBVggGRrzgHBrOcE4qWu5zc3IR2geFJ9wFZSmkjSNvCjYPqR50o47xnriONIulFHnQgeSTBOM7uSceEYHlk+tXuBcg8QuyOlayBdsu46SY9QXxq/DNAyfmCCRI7x3VbyIsdKIyNK/ZGZhs0YABIyPNAoGM5Th1jPcyhIY3lkY5woLsd92b6ZO5O3rXUOE+yu2twJOIXQf/AHduQEJzuplbAJ9VGG74rW8PnCJ0OG2ywxnALKGUttjLSHErnHn4CCO7CgyXL3s3gtAJ+JkPIMEWqEYU4yBO42886BknGwfcVsYree/YDGiFdkVRpCrjThB+j4ds9yMjwqdFOeDcnFiJJzqPlnAAzudIGwydzjud+9bS1tFjGFGKBfwPgcduoAAzTeiigKKKKAooooCiiigKKKKAooooCiiigKKKKCvc2aOMMAazXFOSopN1GD6jY1raKDn/ALhxC3Pw5i49JPH/AIvm/wAVQXXFncab2wjmHYnSrj+66k/466MRUUlqh7qKDkV1wngkp+Jw94j6oJIh+UbsD+VL5uUOAHfVcp9AZj/nCa7HJweI91FV25dgP6I/Kg48nKvAh5XT428RkA/dEKYW3BOBputi8jDtqad/8LMq11FeXIP1R+VTx8FhHZRQc/sLxYv/AAfDo4v2ljjib8dpM/mKuG14hc/OwQZzgAt+I1ltJ+qha3sdmi9lFThQKDGcP5JXVrlJd/NnJZj9yd61Fnw2OMYVRVyigKKKKAooooCiiigKKKKAooooCiiigKKKKAooooCiiigKKKKAooooCiiigKKKKAooooCiiigKKKKAooooCiiigKKKKAooooP/2Q=='
        }, {
          name: 'Diamond',
          description: 'Compilation of customers wit a diamond customer status',
          url: 'data:image/jpeg;base64,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'
        }, {
          name: 'Silver',
          description: 'Compilation of customers wit a silver customer status',
          url: 'data:image/jpeg;base64,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qR50o47xnriONIulFHnQgeSTBOM7uSceEYHlk+tXuBcg8QuyOlayBdsu46SY9QXxq/DNAyfmCCRI7x3VbyIsdKIyNK/ZGZhs0YABIyPNAoGM5Th1jPcyhIY3lkY5woLsd92b6ZO5O3rXUOE+yu2twJOIXQf/AHduQEJzuplbAJ9VGG74rW8PnCJ0OG2ywxnALKGUttjLSHErnHn4CCO7CgyXL3s3gtAJ+JkPIMEWqEYU4yBO42886BknGwfcVsYree/YDGiFdkVRpCrjThB+j4ds9yMjwqdFOeDcnFiJJzqPlnAAzudIGwydzjud+9bS1tFjGFGKBfwPgcduoAAzTeiigKKKKAooooCiiigKKKKAooooCiiigKKKKCvc2aOMMAazXFOSopN1GD6jY1raKDn/ALhxC3Pw5i49JPH/AIvm/wAVQXXFncab2wjmHYnSrj+66k/466MRUUlqh7qKDkV1wngkp+Jw94j6oJIh+UbsD+VL5uUOAHfVcp9AZj/nCa7HJweI91FV25dgP6I/Kg48nKvAh5XT428RkA/dEKYW3BOBputi8jDtqad/8LMq11FeXIP1R+VTx8FhHZRQc/sLxYv/AAfDo4v2ljjib8dpM/mKuG14hc/OwQZzgAt+I1ltJ+qha3sdmi9lFThQKDGcP5JXVrlJd/NnJZj9yd61Fnw2OMYVRVyigKKKKAooooCiiigKKKKAooooCiiigKKKKAooooCiiigKKKKAooooCiiigKKKKAooooCiiigKKKKAooooCiiigKKKKAooooP/2Q=='
        }]
      }
    },
    methods: {
      create () {
        this.$validator.validateAll().then((result) => {
          if (result) {
            this.dialogTableVisible = false
            this.lists.push({ name: this.name, description: this.description })
            sweetalert('Success!', 'Group created!', 'success')
          }
        })
      },
      showForm  () {
        this.isEditing = true
      },
      hideForm () {
        this.isEditing = false
        sweetalert('Success!', 'Groups updated!', 'success')
      }
    }
  }
</script>
<style>
    .padding-fifthin{
            padding: 15px!important;
    }
    .box:hover {
        box-shadow: 5px 5px 5px #d1d1d1
    }
    .title h1{
        color: #000;
    }
    .Groupname{
        color: #000;
    }
    .Groups-list{
        padding: 0;
    }
    .Groups-list li{
        list-style: none;
        margin: 0
    }
    .groupcard{
        margin-top: 22px
    }
    .description h4 {
    text-align:left;
    font-size:14px
    }
    .els{
        margin-top: -30px
    }
    .els button{
        background: none;
        border: 0;
        text-align: right;
    }
    .extras{
        position: relative;
        widows: 200px;
        border: 1px silver #d1d1d1
    }
    .extras ul li{
        list-style: none;
        display: inline;
        text-align: right
    }
    .box{
        border: 1px solid #d1d1d1;
        padding-bottom: 20px
    }
    .next{
        margin-left: -8px
    }
    .form-error{
        color: red
    }
    .my-btn{
        padding: 8px;
        padding-left: 12px;
        padding-right: 12px;
        border-radius: 5px;
        border: 0
    }
</style>