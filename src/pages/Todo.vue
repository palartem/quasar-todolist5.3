<template>
    <q-page class="q-pa-lg bg-grey-3 column">
        <q-list
            separator
            bordered
        >
            <q-item
                v-for="(task, index) in tasks"
                :key="index"
                :class="{'done bg-blue-1': task.done}"
                v-ripple
                clickable
                @click="task.done = !task.done"
            >
                <q-item-section avatar>
                    <q-checkbox
                        v-model="task.done"
                        class="no-pointer-events"
                        val="teal"
                        color="primary"
                    />
                </q-item-section>
                <q-item-section>
                    <q-item-label>{{ task.title }}</q-item-label>
                </q-item-section>
                <q-item-section
                    v-if="task.done"
                    side
                >
                    <q-item-label>
                        <q-btn
                            round
                            flat
                            color="red"
                            icon="delete"
                            size="md"
                            @click.stop="deleteTask(index)"
                        />
                    </q-item-label>
                </q-item-section>
            </q-item>
        </q-list>
    </q-page>
</template>

<script>
export default {
    data() {
        return {
            tasks: [
                {
                    title: 'hello',
                    done: true,
                },
                {
                    title: 'hello2',
                    done: false,
                },
                {
                    title: 'hello3',
                    done: false,
                },
            ],
        };
    },
    methods: {
        deleteTask (index) {
            this.tasks.splice(index, 1)
        }
    },
}

</script>
<style lang="scss">
.done {
    .q-item__label {
        text-decoration: line-through;
        color: $primary;
    }
}
</style>
