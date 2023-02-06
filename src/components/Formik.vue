<template>
    <div>
        <div v-for="(value, key) in initialValues">
            <div>
                <label :for="key">{{ key }}: </label>
                <FieldInput :as="key" :name="key" @update:modelValue="initialValues[key] = $event" />
            </div>
        </div>
        <input type="submit" @click="onSubmit(initialValues)" />
    </div>
</template>

<script>

import FieldInput from './FieldInput.vue';

export default {
    name: 'Formik',
    props: {
        initialValues: {
            type: Object,
            default: () => ({}),
        },
        onSubmit: {
            type: Function,
            default: () => { },
        },
        validate: {
            type: Function,
            default: () => { },
        },
    },
    components: {
        FieldInput,
    }

}

</script>

<style scoped>

</style>
