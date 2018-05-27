<template>
<transition name="el-zoom-in-top">
    <div class="content-wrapper dashboard-wrapper">
        <!-- Main content -->
        <section class="content pie-container">
        <!-- <div class="pull-left page-title"><p><b> Home</b></p> </div> -->
            <div class="row">
                <div class="col-md-12">
                    <div class="col-md-12 top-sect">
                        <div class="container pull-left page-title">
                            <p><b> HOME</b></p> 
                        </div>
                    </div>
                    <div class="col-md-6 pie">
                        <!-- Default box -->
                        <div class="box">
                            <div class="box-body">
                                <div class="text-center"> <p>Delivery Rate</p> </div>
                                <ve-pie :data="chartData1" :settings="chartSettings"></ve-pie>
                            </div>
                            <!-- /.box-body -->
                        </div>
                    </div>
                    <div class="col-md-6 pie">
                        <!-- Default box -->
                        <div class="box">
                            <div class="box-body">
                                <div class="text-center"> <p>Response Rate</p> </div>
                                <ve-pie :data="chartData2" :settings="chartSettings"></ve-pie>
                            </div>
                            <!-- /.box-body -->
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
  module.exports = {
    created: function () {
      this.chartData1 = {
        columns: ['title', 'value'],
        rows: [
          { 'title': 'sent', 'value': 3 },
          { 'title': 'delivered', 'value': 6 },
          { 'title': 'not sent', 'value': 6 }
        ]
      }
      this.chartData2 = {
        columns: ['title', 'value'],
        rows: [
          { 'title': 'Lagos', 'value': 213 },
          { 'title': 'Abuja', 'value': 133 },
          { 'title': 'Kano', 'value': 62 }
        ]
      }
      this.chartSettings = {
        metrics: 'value',
        dimension: 'title'
      }
    }
  }
</script>
<style>
/* .pie{
    margin-top: 50px;
} */
/* .box{
    background-color: #bbb8b8
} */
.box p{
     font-size:20px;
}
.box{
    border: 1px solid #ccc
}
@media  (max-width:767px) {
    ve-pie{
        width: 100%
    }
    .pie-container{
        margin-top: 30px
    }
}
</style>