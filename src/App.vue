<template>
  <div id="app">
    <el-input-number v-model="num1" @change="handleChange" :min="1" :max="10" label="描述文字"></el-input-number>
    <p>小计：{{totalFee}}</p>
    <br>
    <el-switch  v-model="value2"  active-text="按月付费"  inactive-text="按年付费">
    </el-switch>
    <br>
    <el-switch v-model="value1" active-color="#13ce66" inactive-color="#ff4949">
    </el-switch>
    <br>
    <el-checkbox :indeterminate="isIndeterminate" v-model="checkAll" @change="handleCheckAllChange">
      全选
    </el-checkbox>
    <div style="margin: 15px 0;"></div>
    <el-checkbox-group v-model="checkedCities" @change="handleCheckedCitiesChange">
      <el-checkbox v-for="city in cities" :label="city" :key="city">{{city}}</el-checkbox>
    </el-checkbox-group>
    <el-checkbox-group v-model="checkList">
      <el-checkbox label="复选框 A"></el-checkbox>
      <el-checkbox label="复选框 B"></el-checkbox>
      <el-checkbox label="复选框 C"></el-checkbox>
      <el-checkbox label="禁用" disabled></el-checkbox>
      <el-checkbox label="选中且禁用" disabled></el-checkbox>
    </el-checkbox-group>
    <el-radio-group v-model="radio">
      <el-radio :label="3" disabled>备选项</el-radio>
      <el-radio :label="6">备选项</el-radio>
      <el-radio :label="9">备选项</el-radio>
    </el-radio-group>
    <el-button type="success" @click="submitRadio">提交</el-button>
    <pre>{{$data}}</pre>
    <br>------------------------------------------------------------------------
    <el-row :gutter="10">
      <el-col :xs="8" :sm="6" :md="4" :lg="3" :xl="1">
        <div class="grid-content bg-purple">
          初学ElementUi
        </div>
      </el-col>
      <el-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11">
        <div class="grid-content bg-purple-light">
          初学ElementUi
        </div>
      </el-col>
      <el-col :xs="4" :sm="6" :md="8" :lg="9" :xl="11">
        <div class="grid-content bg-purple">
          初学ElementUi
        </div>
      </el-col>
      <el-col :xs="8" :sm="6" :md="4" :lg="3" :xl="1">
        <div class="grid-content bg-purple-light">
          初学ElementUi
        </div>
      </el-col>
    </el-row>
    ------------------------------------------------------------------------
    <el-row>
      <el-col :span="8">
        <div class="grid-content bg-purple">
          初学ElementUi
        </div>
      </el-col>
      <el-col :span="8">
        <div class="grid-content bg-purple-light">
          <img src="./assets/logo.png">
          <div>
            <el-button type="primary" @click="startHacking">Start</el-button>
          </div>
        </div>
      </el-col>
      <el-col :span="8">
        <div class="grid-content bg-purple">
          初学ElementUi
        </div>
      </el-col>
    </el-row>
  
  </div>
</template>

<script>
const cityOptions = ['上海', '北京', '广州', '深圳'];

export default {
 data () {
    return {
      radio: 3,
      checkList: ['选中且禁用','复选框 A'],
      checkAll: false,
      checkedCities: ['上海', '北京'],
      cities: cityOptions,
      isIndeterminate: true,
      value1: true,
      value2: true,
      num1: 1,
      price:100
    };
  },
  computed:{
    totalFee(){
      return this.num1*this.price;
    }
  },
  methods: {
    handleChange(value) {
      console.log(value);
    },
    handleCheckAllChange(val) {
      this.checkedCities = val ? cityOptions : [];
      this.isIndeterminate = false;
    },
    handleCheckedCitiesChange(value) {
      let checkedCount = value.length;
      this.checkAll = checkedCount === this.cities.length;
      this.isIndeterminate = checkedCount > 0 && checkedCount < this.cities.length;
    },
    submitRadio(){
      this.$notify({
        title: '你选择的是'+this.radio,
        type: 'success',
        message: 'We\'ve laid the ground work for you. It\'s time for you to build something epic!',
        duration: 5000
      })
    },
    startHacking () {
      this.$notify({
        title: 'It works!',
        type: 'success',
        message: 'We\'ve laid the ground work for you. It\'s time for you to build something epic!',
        duration: 5000
      })
    }
  }
}
</script>

<style>
#app {
  font-family: Helvetica, sans-serif;
  text-align: center;
}



 .el-col {
    border-radius: 4px;
  }
  .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  }
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
</style>
