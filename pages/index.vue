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
                formProps:  {
                    // id: 1,
                    // name: 'iPhone 13 128 ГБ черный',
                    // image: 'https://c.dns-shop.ru/thumb/st1/fit/500/500/484b878691d685e6045bb0b2de36f9d2/c201023fee63375d614103f3eb86c77160656dae59094cd22a883302c5144fbc.jpg',
                    // price: 2326,
                    // description: 'Смартфон Apple iPhone 13 со 128 ГБ постоянной памяти',
                }
            }
        }
}
</script>
