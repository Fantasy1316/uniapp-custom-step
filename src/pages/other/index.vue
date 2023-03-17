<template>
  <view class="container">
    <view class="coustom-step">
      <view class="coustom-step-item" v-for="item in steps" :key="item.index" :class="{ 'coustom-step-item_active': currentStep === item.index }" @click="currentStep = item.index">
        <text class="item-name">{{ item.name }}</text>
      </view>
    </view>

    <view class="next">Next >></view>
  </view>
</template>

<script>
export default {
  data() {
    return {
      steps: [
        {
          index: 0,
          name: '第一步'
        },
        {
          index: 1,
          name: '第二步'
        },
        {
          index: 2,
          name: '第三步'
        },
        {
          index: 3,
          name: '第四步'
        }
      ],
      currentStep: 0
    }
  },
  methods: {
    handToNext() {
      uni.navigateTo({
        url: '/pages/index/index'
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  width: 100%;
  height: 100vh;
  background-color: #fff;

  .coustom-step {
    display: flex;
    padding: 20rpx 48rpx 20rpx 24rpx;

    &-item {
      flex: 1;
      display: flex;
      justify-content: center;
      align-items: center;
      position: relative;
      height: 68rpx;
      font-size: 24rpx;
      color: #333;
      background-color: #f8f8f8;

      .item-name {
        position: relative;
        z-index: 2;
      }

      &::after {
        content: '';
        position: absolute;
        width: 48rpx;
        height: 48rpx;
        right: -24rpx;
        background-color: #f8f8f8;
        transform: rotate(45deg);
        z-index: 1;
        box-shadow: 6rpx -6rpx 2rpx 2rpx #fff;
      }

      &:not(:first-child) {
        text-indent: 40rpx;
      }

      &_active {
        background-color: #53afff;

        .item-name {
          color: #fff;
        }

        &::after {
          background-color: #53afff;
        }
      }
    }
  }

  .next {
    padding: 20rpx;
    font-size: 28rpx;
    color: #5da0ff;
    text-align: center;
  }
}
</style>
