<template>
  <section class="section">
    <div class="columns is-mobile">

      <card
        title="Добавить товар"
        icon="cellphone-link"
      >
       <section>
        <b-button
            label="Добавить новый товар"
            type="is-primary"
            size="is-medium"
            @click="isComponentModalActive = true" />

        <b-modal
            v-model="isComponentModalActive"
            has-modal-card
            full-screen
            :can-cancel="false">
            <modal-form v-bind="formProps"></modal-form>
        </b-modal>
    </section>
      </card>

    </div>
  </section>
</template>

<script>
import Card from '~/components/Card'
import ModalForm from '~/components/ModalForm'

    export default {
        name: 'IndexPage',
        components: {
            ModalForm,
            Card
        },
        data() {
            return {
                isComponentModalActive: false,
                formProps: {
                    email: 'evan@you.com',
                    password: 'testing'
                }
            }
        }
}
</script>
