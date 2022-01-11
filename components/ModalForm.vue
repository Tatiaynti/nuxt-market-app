<template>
  <div class="modal-card" style="width: auto">
                <header class="modal-card-head">
                    <p class="modal-card-title">Заполните карточку товара</p>
                </header>
                <section class="modal-card-body">
                    <b-field label="Название">
                        <b-input type="text" name="name"
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
            <b-input placeholder="Цена товара" name="price"
                type="number"
                min="0"
                required>
            </b-input>
        </b-field>
          <b-field label="Описание товара">
            <b-input maxlength="500" type="textarea" name="description"></b-input>
        </b-field>
                </section>
                <footer class="modal-card-foot">
                    <b-button
                        label="Отменить"
                        @click="$parent.close()" />
                    <b-button
                        label="Отправить"
                        type="is-primary"
                        @click="storeData()"
                         />
                </footer>
            </div>
</template>

<script>

export default {
  name: 'ModalForm',
  data() {
    return {
      isComponentModalActive: false,
      formProps: {
        // id: 1,
        // name: '',
        // image: 'https://c.dns-shop.ru/thumb/st1/fit/500/500/484b878691d685e6045bb0b2de36f9d2/c201023fee63375d614103f3eb86c77160656dae59094cd22a883302c5144fbc.jpg',
        // price: 2326,
        // description: 'Смартфон Apple iPhone 13 со 128 ГБ постоянной памяти',
      },
      methods: {
        deleteDropFile(index) {
          this.dropFiles.splice(index, 1)
        }
      },
        storeData() {
            if (window.localStorage) {
                const elements = document.querySelectorAll('[name]');

                for (let i = 0, length = elements.length; i < length; i++) {
                    (function(element) {
                        const name = element.getAttribute('name');

                        element.value = localStorage.getItem(name) || '';

                        element.onkeyup = function() {
                            localStorage.setItem(name, element.value);
                        };
                    })(elements[i]);
                }
            }
        }
    }
  }
}
</script>

