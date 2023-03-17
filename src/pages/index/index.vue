<template>
  <view class="container">
    <view class="coustom-step">
      <view class="coustom-step-item" v-for="item in steps" :class="{ 'coustom-step-item_active': currentStep === item.index }" :key="item.index" @click="currentStep = item.index">
        <view class="item-before"></view>
        <view class="item-name">{{ item.name }}</view>
        <view class="item-after"></view>
      </view>
    </view>

    <view class="next" @click="handToNext">Next >></view>
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
        url: '/pages/other/index'
      })
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  width: 100%;
  min-height: 100vh;
  background-color: #f8f8f8;

  --default-color: #dfdfdf;
  --active-color: #5da0ff;

  .coustom-step {
    display: flex;
    padding: 20rpx 40rpx;
    box-sizing: border-box;
    background-color: #fff;

    &-item {
      flex: 1;
      display: flex;
      flex-direction: column;
      position: relative;
      height: 68rpx;
      font-size: 24rpx;

      .item-after {
        flex: 1;
        width: 95%;
        height: 34rpx;
        background-color: var(--default-color);
        transform: skewX(-30deg);
      }

      .item-before {
        width: 95%;
        height: 34rpx;
        background-color: var(--default-color);
        transform: skewX(30deg);
      }

      .item-name {
        display: flex;
        justify-content: center;
        align-items: center;
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        color: #8d8d8d;
        z-index: 1;
      }

      &:first-child {
        .item-name {
          left: -10rpx;
        }

        .item-before,
        .item-after {
          &::before {
            content: '';
            position: absolute;
            width: 34rpx;
            height: 34rpx;
            left: -10rpx;
            background-color: var(--default-color);
          }
        }

        .item-before {
          &::before {
            transform: skewX(-30deg);
          }
        }

        .item-after {
          &::before {
            transform: skewX(30deg);
          }
        }
      }

      &_active {
        .item-before,
        .item-after {
          background-color: var(--active-color) !important;

          &::before {
            background-color: var(--active-color) !important;
          }
        }

        .item-name {
          color: #fff;
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
