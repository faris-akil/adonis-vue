<template lang="html">
  <v-layout row wrap>
    <v-flex xs9 class="text-xs-left">
      <slot></slot>
      <span @click="$emit('onClick')" v-if="!isEditMode">
        {{title}}
      </span>
      <v-text-field
        v-if="isEditMode" :value="title" @keyup.enter="$emit('onSave')" @input="$emit('onInput', $event)">

      </v-text-field>
    </v-flex>
    <v-flex xs3 class="text-xs-right">
      <v-icon @click="$emit('onEdit')" v-if="!isEditMode">edit</v-icon>
      <v-icon @click="$emit('onSave')" v-if="isEditMode">check</v-icon>
      <v-icon @click="$emit('onDelete')" >delete</v-icon>
    </v-flex>
  </v-layout>
</template>

<script>
export default {
  props: [
    'isEditMode',
    'title',
    'record',
  ]
};
</script>

<style lang="css">
</style>
