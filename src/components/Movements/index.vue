<template>
  <div class="movements">
    <h2 class="title">Historial</h2>
    <div class="content">
      <Movement v-for="{id, title, description, amount} in movements" 
      :key="id" 
      :id="id"
      :description="description"
      :title="title"
      :amount="amount" 
      @remove="remove"
      />
    </div>

  </div>
</template>

<script setup>
import { toRefs, defineProps , defineEmits} from 'vue';
import Movement from './Movement.vue';

const props = defineProps({
  movements: {
    type: Array,
    default: () => [],
  }
});

const emits = defineEmits(["remove"])


const remove = (id) => {
  console.log("remove", id)
  emits("remove", id)
}

const { movements } = toRefs(props);

</script>
<style scoped>
.movements {
  max-height: 100%;
  padding: 0 8px;
  margin-bottom: 14px;
}

.title {
  margin: 8px 16px 24px 16px;
  color: var(--brand-blue);
}

.content {
  max-height: 68vh;
  display: flex;
  flex-direction: column;
  gap: 8px;
  overflow-y: scroll;
}
</style>
