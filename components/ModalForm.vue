<template>
  <div class="modal-card" style="width: auto">
                <header class="modal-card-head">
                    <p class="modal-card-title">Заполните карточку товара</p>
                </header>
                <section class="modal-card-body">
                    <b-field label="Название">
                        <b-input type="text"
                :lazy="beLazy"
                v-model="value"
                placeholder="Название товара"
                required>
            </b-input>
                    </b-field>

                      <b-field>
            <b-upload v-model="dropFiles"
                multiple
                drag-drop>
                <section class="section">
                    <div class="content has-text-centered">
                        <p>
                            <b-icon
                                icon="upload"
                                size="is-large">
                            </b-icon>
                        </p>
                        <p>Загрузите фото товара</p>
                    </div>
                </section>
            </b-upload>
        </b-field>

        <div class="tags">
            <span v-for="(file, index) in dropFiles"
                :key="index"
                class="tag is-primary" >
                {{file.name}}
                <button class="delete is-small"
                    type="button"
                    @click="deleteDropFile(index)">
                </button>
            </span>
        </div>

                    <b-field label="Цена">
            <b-input placeholder="Цена товара"
                type="number"
                min="0"
                required>
            </b-input>
        </b-field>
          <b-field label="Описание товара">
            <b-input maxlength="500" type="textarea"></b-input>
        </b-field>
                </section>
                <footer class="modal-card-foot">
                    <b-button
                        label="Отменить"
                        @click="$parent.close()" />
                    <b-button
                        label="Отправить"
                        type="is-primary" />
                </footer>
            </div>
</template>

<script>
const ModalForm = {
        props: ['email', 'password'],
    }

export default {
 data() {
            return {
                isComponentModalActive: false,
                formProps: {
                    email: 'evan@you.com',
                    password: 'testing'
                },
                methods: {
            deleteDropFile(index) {
                this.dropFiles.splice(index, 1)
            }
        }
            }
        }
}
</script>

