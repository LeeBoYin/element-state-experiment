<script setup>
const num = 10;
</script>

<template>
  <div class="container">
    <button
        v-for="i in num"
        class="btn"
        tabindex="1"
        :disabled="i === num"
    ></button>
  </div>
</template>

<style lang="scss">
.container {
  display: grid;
  gap: 12px
}
.btn {
  --state-text: 'default';
  display: block;
  padding: 20px;
  border: 1px solid #333;
  border-radius: 4px;
  background-color: #eeeeee;
  user-select: none;
  transition: transform .1s ease-out;
  &:after {
    content: var(--state-text);
  }

  &:disabled {
    --state-text: 'disabled';
    color: #cccccc;
  }

  &:not(:disabled) {
    cursor: pointer;

    // hover
    @media (hover: hover) {
      &:hover {
        --state-text: 'hover';
        background-color: #cccccc;
        transform: translateY(-2px);
      }
    }

    // active
    &:active {
      --state-text: 'active';
      background-color: #333333;
      color: #ffffff;
      transform: translateY(4px);
    }

    // focus
		&:focus:not(.focus-visible) { // remove outline for non-keyboard :focus
      outline: none;
    }
    &:focus-visible { // focus with keyboard tab
      outline: 3px dashed red;
      outline-offset: 3px;
    }
  }
}
</style>
