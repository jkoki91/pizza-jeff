<template>
  <div
    v-if="OpenClose"
    class="modal fade show opacity-50"
    tabindex="-1"
    aria-labelledby="staticBackdropLabel"
    aria-modal="true"
    role="dialog"
    style="display: block"
    data-bs-backdrop="static"
    data-bs-keyboard="false"
    aria-hidden="true"
    id="modal__container"
  ></div>
  <div
    v-if="OpenClose"
    class="modal fade show"
    tabindex="-1"
    aria-labelledby="staticBackdropLabel"
    aria-modal="true"
    role="dialog"
    style="display: block"
    data-bs-backdrop="static"
    data-bs-keyboard="false"
    aria-hidden="true"
  >
    <div class="modal-dialog modal-dialog-centered" id="modal__body">
      <div class="modal-content">
        <div class="modal-header">
          <h3>
            {{ customerInfo.customerName }} {{ customerInfo.customerLastName }}
          </h3>
          <button
            type="button"
            @click="$emit('closeFun')"
            class="btn-close"
          ></button>
        </div>
        <div class="d-flex flex-direction-row">
            <img 
            src="https://www.creativosonline.org/wp-content/uploads/2010/05/creativosonline_crear_avatar_profesional.jpg.webp" 
            alt="Imagen de usuario"
            class="client__img"
            >
            <div class="modal-body">
              <p>Phone number: {{ chunk(customerInfo.customerPhoneNumber) }}</p>
              <p>e-mail: {{ customerInfo.customerEmail }}</p>
              <p>Address: Calle falsa 123 </p>
              <slot></slot>
            </div>
        </div>
        <div class="modal-footer"></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "UserInfo",
  emits:["closeFun"],
  props: {
    visible: Boolean,
    variant: String,
    customerInfo: Object
  },
  data() {
    return {
      OpenClose: this.visible,
    };
  },
  methods: {
      chunk(items) {//split phone number
            let phone =''
            let three = ''
            for(let i=0 ; i<12 ; i=i+3){
                three = ''
                for (let j = i; j<i+3; j++) {
                    // console.log(j)
                    three=three+items.charAt(j)
                }
                phone = phone +' '+ three
            }
            return phone
        }
  },
  watch: {
    visible: function (Val) {
      // watch it
      this.OpenClose = Val
      console.log(this.customerInfo)
    },
  },
};
</script>

<style scoped>

#modal__container {
    background-color: black;
}

.client__img{
    width: 30%;
    height: auto;
    margin: 1rem;
}
</style>