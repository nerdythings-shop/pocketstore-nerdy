<template>
  <button class="btn btn-secondary join-item" @click="addToCart(product.id)">
    {{ $t('checkout.add-to-cart') }}
  </button>

  <!-- Put this part before </body> tag -->
  <input type="checkbox" v-model="modal" class="modal-toggle"/>
  <div class="modal" role="dialog">
    <div class="modal-box">
      <h3 class="text-lg font-bold">Add to Cart modal</h3>
      <p class="py-4">Danke das sie sich für ein Produkt entschieden haben.
        Wollen sie weiter shoppen oder zum Warenkorb</p>
      <section class="actions flex justify-end">
        <a href="/de/checkout" class="btn btn-primary">Warenkorb</a>
        <a href="/" class="btn btn-secondary">Weiter shoppen</a>
      </section>
    </div>
    <label class="modal-backdrop" @click="modal = false">Close</label>
  </div>
</template>

<script lang="ts" setup>
import {useLocalStorage} from "@vueuse/core";
import {addToast} from "@/utils/toast";
import {onMounted} from "vue";

const {product} = defineProps({
  product: {
    type: Object,
    required: true,
  },
});

onMounted(() => {
  modal.value = false;
})

const modal = useLocalStorage("modal-" + product.id, false);

const cart = useLocalStorage("cart", [], {});

const addToCart = async (id, qty = 1) => {
  if (!cart.value) {
    cart.value = [];
  }
  const existingItem = cart.value.find((item) => item.id === id);
  if (existingItem == undefined) {
    cart.value.push({id, qty, product});
  } else {
    const index = cart.value.findIndex(toast => toast.id === existingItem.id);
    cart.value[index].qty = qty;
  }
  navigator.serviceWorker.ready.then((registration) => {
    registration.showNotification("NerdyThings.shop", {
      silent: false,
      icon: '/nerdy-logo-symbol.svg',
      body: 'Produkt zum Warenkorb hinzugefügt: ' + existingItem.id + ' => Anzahl: ' + qty,
    });
    if ("vibrate" in navigator) {
      // Vibrate for 200ms
      navigator.vibrate([200, 100, 200, 100, 200, 100, 200]);
    }
  });
  // TOOD mobile push message
  addToast('Produkt zum Warenkorb hinzugefügt: ' + existingItem.id + ' => Anzahl: ' + qty, 'success');
  modal.value = true;
};
</script>