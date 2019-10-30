<template>
     <div>
            <button @click='subevent' class="btn btn-info btn-sm">-</button>
            {{count}}
            <button @click='addevent' class="btn btn-info btn-sm">+</button>
        </div>
</template>

<script>
export default {
     props: ['count', 'ind'],
      data() {
            return {

            }
        },
        methods: {
            addevent() {
                this.$emit('add-count', this.ind)
            },
            subevent() {
                this.$emit("sub-count", this.ind)
            },
        }
}
</script>

<style>

</style>