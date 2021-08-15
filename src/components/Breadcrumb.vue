<template>
  <nav>
    <ol class="breadcrumb">
      <li
        v-for="(crumb, index) in crumbs"
        :key="index"
        class="breadcrumb-item align-items-center"
      >
        <div class="link" :class="{ disabled: isLast(index) }" @click="selected(crumb)">
          {{ crumb }}
        </div>
      </li>
    </ol>
  </nav>
</template>

<script>
export default {
  props: {
    crumbs: {
      type: Array,
      required: true,
    },
  },
  methods: {
    isLast(index) {
      return index === this.crumbs.length - 1;
    },
    selected(crumb) {
      this.$emit('selected', crumb);
    },
  },
};
</script>
 
<style scoped>
.breadcrumb {
  background-color: white;
  display: flex;

}

/* .breadcrumb-item{
  margin-right: 1.2rem;
} */

ol{
  list-style: none;
}

.breadcrumb-item:not(:last-child){
  color: #5673A8;
  font-size: 17px;
  font-weight: 500;
  cursor: pointer;
}

.breadcrumb-item:not(:last-child):hover {
  text-decoration: underline;
}


.link:before {
  padding: 8px;
  color: black;
  content: "/\00a0";
}
</style>