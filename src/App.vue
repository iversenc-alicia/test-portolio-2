<script setup>
import { RouterLink, RouterView } from 'vue-router'
import { supabase, isConnect } from '@/supabase.js'

import footerE from './components/footer.vue'

import { ref } from 'vue';
const menuVisible = ref(true);

const SignOut = async () => {
  const { error } = await supabase.auth.signOut();
  if (error) throw error;
  // route.push("/")
  isConnect.value = !isConnect.value;
}

console.log("user est", isConnect)

</script>

<template>
  <div class="bg-edark">

    <header>


    </header>

    <Suspense>
      <RouterView :class="{ hidden: !menuVisible }" />
    </Suspense>

    <footerE :class="{ hidden: !menuVisible }" />
  </div>

</template>