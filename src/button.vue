<template>
  <button class="g-button" :class="{[`iconPos-${iconPosition}`]: true}">
    <i :class="['iconfont', 'lunzi-icon', 'icon-'+icon]" v-if="icon"></i>
    <div class="content">
      <slot></slot>
    </div>
    
  </button>
</template>

<script>
export default {
  props: {
    icon: '',
    iconPosition: {
      type: String,
      default: 'left',
      validator(value) {
        return (value === 'left' || value === 'right')
      }
    }
  }
}

</script>
<style lang='scss' scoped>
    .g-button {
      cursor: pointer;
      font-size: var(--font-size);
      height: var(--button-height);
      padding: 0 1em;
      border-radius: var(--border-radius);
      border: 1px solid var(--border-color);
      background: var(--button-bg);
      display: inline-flex;
      justify-content: center;
      align-items: center;
      &:hover {
        border-color: var(--border-color-hover);
      }
      &:active {
        background: var(--button-active-bg);
      }
      &:focus {
        outline: none;
      }

      &>.content {
        order: 2;
      }
      &>.lunzi-icon {
        order: 1;
        margin-right: .1rem;
      }
      &.iconPos-right {
        &>.content {
          order: 1;
        }
        &>.lunzi-icon {
          order: 2;
          margin-left: .1rem;
          margin-right: 0;
        }
      }
    }

    
</style>