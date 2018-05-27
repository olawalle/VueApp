<template>
    <div class="content-wrapper">
        <!-- Content Header (Page header) -->
        <section class="content-header">
            <h1>EChart Pie <small><i class="ti-heart"></i><i class="ti-export"></i><i class="ti-printer"></i></small></h1>
            <ol class="breadcrumb">
                <li>
                    <router-link to="/"> <i class="ti-home"></i></router-link>
                </li>
                <li><a href="#">Charts</a></li>
                <li class="active">EChart Pie</li>
            </ol>
        </section>
        <!-- Main content -->
        <section class="content">
            <div class="row">
                <div class="col-md-12">
                    <!-- Default box -->
                    <div class="box">
                        <div class="box-body">
                            <ve-pie :data="chartData" :settings="chartSettings"></ve-pie>
                        </div>
                        <!-- /.box-body -->
                    </div>
                </div>
            </div>
        </section>
        <!-- /.content -->
    </div>
</template>
<script>
  module.exports = {
    created: function () {
      this.chartData = {
        columns: ['Others'],
        rows: [
          { 'Others': 3 },
          { 'Others': 6 },
          { 'Others': 90 },
          { 'Others': 12 },
          { 'Others': 15 },
          { 'Others': 20 }
        ]
      }
      this.chartSettings = {
      }
    }
  }
</script>