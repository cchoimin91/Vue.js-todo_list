<template>
  <section>
    <ul>
      <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
        {{todoItem}}
        <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
          <i class="far fa-trash-alt" aria-hidden="true"></i>
        </span>
      </li>
    </ul>
  </section>
</template>

<script>
  export default{
    props :['propsdata'],



    methods : {
      removeTodo(todoItem, index) {
        this.$emit('removeTodo', todoItem, index);
      }
    }
  }
</script>

<style>
ul{
  list-style-type: none;
  padding-left: 0px;
  margin-top: 0;
  text-align: left;
}

li{
  display: flex;
  min-height: 50px;
}
</style>
