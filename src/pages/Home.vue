<template>
<div id="box">
  <!-- 头部 -->
  <header class="head">
    <Icon class="icon" type="ios-arrow-back" />
    <div class="head-text">新增预约</div>
  </header>
  <!-- 主体部分 -->
  <body>
    <!-- 行程选择 -->
    <Row class="route-box" type="flex" align="middle">
      <i-col span="11">
        <Button type="text" size="long">{{placeOfDeparture}}</Button>
      </i-col>
      <i-col span="2">
        <Icon type="md-repeat" size="28" color="#CBCBCB" />
      </i-col>
      <i-col span="11">
        <Button type="text" size="long">{{destination}}</Button>
      </i-col>
    </Row>

    <!-- <i-col span="10">
        <DatePicker type="date" :options="options1" placeholder="最早出发时间" style="width: 150px"></DatePicker>
      </i-col>
      <i-col span="4">
        <Icon type="ios-remove" />
      </i-col>
      <i-col span="10">
        <DatePicker type="date" :options="options1" placeholder="最早出发时间" style="width: 150px"></DatePicker>
    </i-col>-->

    <!-- 时间选择 -->
    <Row class="data-box" type="flex" align="middle">
      <i-col span="11">
        <Button type="text" size="long">{{pioneerData}}</Button>
      </i-col>
      <i-col span="2">
        <Icon type="md-remove" size="28" color="#CBCBCB" />
      </i-col>
      <i-col span="11">
        <Button type="text" size="long">{{atLatestData}}</Button>
      </i-col>
    </Row>

    <!--出行原因 -->
    <Row class="routeCause-box" type="flex" align="middle">
      <i-col class="input-text" span="6">出行原因</i-col>
      <i-col span="16">
        <Select v-model="model1" style="width:100%">
          <Option v-for="item in routeCause" :value="item.value" :key="item.value">{{ item.label }}</Option>
        </Select>
      </i-col>
    </Row>

    <!-- 车票价格 -->
    <Row class="pice-box" type="flex" align="middle">
      <i-col class="input-text" span="6">车票价格</i-col>
      <i-col span="16">
        <input class="inp" type="text" placeholder="请输入" />
      </i-col>
    </Row>

    <!-- 车型 -->
    <Row class="carType" type="flex" align="middle">
      <i-col class="input-text" span="6">车型</i-col>
      <i-col span="16">
        <Select placeholder="经济" v-model="model1" style="width:100%">
          <Option v-for="item in carlist" :value="item.value" :key="item.value">{{ item.label }}</Option>
        </Select>
      </i-col>
    </Row>

    <!-- 备注 -->
    <Row class="remark" type="flex" align="middle">
      <i-col class="input-text" span="6">预约备注</i-col>
      <i-col span="16">
        <input class="inp" type="text" placeholder="请输入" />
        <!-- <Input v-model="value2" placeholder="请输入" /> -->
      </i-col>
    </Row>

    <!-- 乘客 -->
    <div class="people">
      <div class="people-text">乘客</div>
      <Row class="tab-box">
        <i-col class="tab" span="7">李佳佳</i-col>  
        <i-col class="tab" span="7">李佳佳</i-col>
        <i-col class="tab" span="7">王思雨</i-col>
        <i-col class="tab" span="7">王思雨</i-col>
        <i-col class="tab" span="7">王思雨</i-col>
        <i-col class="tab" span="7">王思雨</i-col>
        <i-col class="addtab" span="7">+添加乘客</i-col>
      </Row>
    </div>

    <!-- 发布 -->
    <div class="issue">
      <Button class="btn1" type="primary" shape="circle">存为草稿</Button>
      <Button class="btn2" type="primary" shape="circle">发布</Button>
    </div>
  </body>
</div>
</template>

<script>
export default {
  data() {
    return {
      placeOfDeparture: "出发地",
      destination: "目的地",
      pioneerData: "最早出发时间",
      atLatestData: "最晚出发时间",
      routeCause: [
        //出行原因
        {
          value: "home",
          label: "家校往返"
        },
        {
          value: "travel",
          label: "旅游"
        },
        {
          value: "else",
          label: "其他"
        }
      ],
      carlist: [
        //车型选择
        {
          value: "economical",
          label: "经济"
        },
        {
          value: "comfort",
          label: "舒适"
        },
        {
          value: "luxury ",
          label: "豪华"
        }
      ],
      count: []
    };
  },
  methods: {
    handleAdd() {
      if (this.count.length) {
        this.count.push(this.count[this.count.length - 1] + 1);
      } else {
        this.count.push(0);
      }
    },
    handleClose2(event, name) {
      const index = this.count.indexOf(name);
      this.count.splice(index, 1);
    }
  }
};
</script>

<style lang='less'  scoped>
input::-webkit-input-placeholder {
  color: #cbcbcb;
}
input::-moz-placeholder {
  /* Mozilla Firefox 19+ */
  color: #cbcbcb;
}
input:-moz-placeholder {
  /* Mozilla Firefox 4 to 18 */
  color: #cbcbcb;
}
input:-ms-input-placeholder {
  /* Internet Explorer 10-11 */
  color: #cbcbcb;
}

#box {
  width: 100%;
  height: 100%;
  .head {
    height: 50px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 5px 0;
    border-bottom: 6px solid #f5f6f8;
    .icon {
      width: 40px;
      text-align: center;
      font-size: 28px;
    }
    .head-text {
      flex: 1;
      text-align: center;
      font-size: 18px;
      font-weight: 600;
      padding-right: 40px;
    }
  }
  body {
    //行程
    .route-box {
      height: 60px;
      border-bottom: 1px solid #cbcbcb;
      button {
        font-size: 20px;
        color: #cbcbcb;
        font-weight: 400;
      }
    }
    //时间
    .data-box {
      height: 60px;
      border-bottom: 6px solid #f5f6f8;
      button {
        font-size: 20px;
        color: #cbcbcb;
      }
    }
    //原因&价格
    .routeCause-box,
    .pice-box {
      height: 60px;
      border-bottom: 1px solid #f5f6f8;
      .input-text {
        color: #4f4f4f;
        margin-left: 8px;
        font-size: 15px;
        font-weight: 800;
      }
      .inp {
        width: 100%;
        height: 30px;
        border: none;
        color: #555;
        text-indent: 10px;
      }
    }
    //车型&备注
    .remark,
    .carType {
      height: 60px;
      border-bottom: 6px solid #f5f6f8;
      .input-text {
        color: #4f4f4f;
        margin-left: 8px;
        font-size: 15px;
        font-weight: 800;
      }
      .ipnt111::input-placeholder {
        color: #dbdbdb;
      }
      .inp {
        width: 100%;
        height: 30px;
        border: none;
        color: #555;
        text-indent: 10px;
      }
    }
    //乘客
    .people {
      padding-top: 20px 0;
      .people-text {
        height: 40px;
        font-size: 18px;
        line-height: 40px;
        font-weight: 600;
        padding-left: 8px;
        color: #646464;
      }
      .tab-box {
        display: flex;
        justify-content: center;
        flex-wrap: wrap;

        .tab {
          color: #8f8f8f;
          font-size: 14px;
          height: 40px;
          border-radius: 5px;
          border: 1px solid #cbcbcb;
          text-align: center;
          line-height: 40px;
          margin: 5px;
        }
        .addtab {
          color: #24c678;
          font-size: 14px;
          height: 40px;
          border-radius: 5px;
          border: 1px dashed #cbcbcb;
          text-align: center;
          line-height: 40px;
          margin: 5px;
        }
      }
    }
    //提交
    .issue {
      position: fixed;
      width: 100%;
      bottom: 0px;
      padding-top: 20px;
      height: 100px;
      background: #f5f6f8;
      display: flex;
      justify-content: space-around;
      .btn1 {
        width: 40%;
        height: 40px;
        background: #fff;
        color: #24c678;
        border: 1px solid #24c678;
      }
      .btn2 {
        width: 40%;
        height: 40px;
        background: #24c678;
        color: #fff;
      }
    }
  }
}
</style>