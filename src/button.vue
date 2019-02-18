<template>
  <button class="g-button" :class="{[`iconPos-${iconPosition}`]: true}" @click="$emit('click')">
    <g-icon :name="icon" v-if="icon && !loading"></g-icon>
    <g-icon name="loading" class="loading" v-if="loading"></g-icon>
    <div class="content">
      <slot></slot>
    </div>
  </button>
</template>

<script>
export default {
  props: {
    icon: {},
    loading: {
      type: Boolean,
      default: false
    },
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
    @keyframes spin {
      0% { transform: rotate(0deg) }
      100% { transform: rotate(360deg) }
    }
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

      .loading {
        animation: spin 1.2s infinite linear;
      }
    }

    
</style>