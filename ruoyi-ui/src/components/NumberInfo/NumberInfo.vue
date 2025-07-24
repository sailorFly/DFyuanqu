<template>
  <div :class="[prefixCls]">
    <slot name="subtitle">
      <div :class="[`${prefixCls}-subtitle`]">{{ typeof subTitle === 'string' ? subTitle : subTitle() }}</div>
    </slot>
    <div class="number-info-value">
      <span>{{ total }}</span>
      <span class="sub-total">
        {{ subTotal }}
        <icon :type="`caret-${status}`" />
      </span>
    </div>
  </div>
</template>

<script>
import { Icon } from 'ant-design-vue'

export default {
  name: 'NumberInfo',
  props: {
    prefixCls: {
      type: String,
      default: 'ant-pro-number-info'
    },
    total: {
      type: Number,
      required: true
    },
    subTotal: {
      type: Number,
      required: true
    },
    subTitle: {
      type: [String, Function],
      default: ''
    },
    status: {
      type: String,
      default: 'up'
    }
  },
  components: {
    Icon
  },
  data () {
    return {}
  }
}
</script>

<style lang="less" scoped>
  @ant-pro-prefix: ant-pro;

  @numberInfo-prefix-cls: ~"@{ant-pro-prefix}-number-info";

  .@{numberInfo-prefix-cls} {

    .ant-pro-number-info-subtitle {
      color: rgba(0, 0, 0, 0.45);
      font-size: 14px;
      height: 22px;
      line-height: 22px;
      overflow: hidden;
      text-overflow: ellipsis;
      word-break: break-all;
      white-space: nowrap;
    }

    .number-info-value {
      margin-top: 4px;
      font-size: 0;
      overflow: hidden;
      text-overflow: ellipsis;
      word-break: break-all;
      white-space: nowrap;

      & > span {
        color: rgba(0, 0, 0, 0.85);
        display: inline-block;
        line-height: 32px;
        height: 32px;
        font-size: 24px;
        margin-right: 32px;
      }

      .sub-total {
        color: rgba(0, 0, 0, 0.45);
        font-size: 16px;
        vertical-align: top;
        margin-right: 0;
        i {
          font-size: 12px;
          transform: scale(0.82);
          margin-left: 4px;
        }
        :global {
          .anticon-caret-up {
            color: #f5222d;
          }
          .anticon-caret-down {
            color: #52c41a;
          }
        }
      }
    }
  }
</style>
