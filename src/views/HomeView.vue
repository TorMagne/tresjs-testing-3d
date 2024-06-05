<template>
  <TresCanvas clear-color="#82DBC5" window-size>
    <Stats />
    <TresPerspectiveCamera />
    <OrbitControls />
    <TresMesh :position="[0, 0, 0]" ref="torusRef">
      <TresTorusKnotGeometry :args="[1, 0.3, 100, 16]" />
      <TresMeshNormalMaterial />
    </TresMesh>

    <TresAxesHelper />
  </TresCanvas>
</template>

<script setup>
  import { useRenderLoop, useTres } from '@tresjs/core';
  import { shallowRef, watchEffect } from 'vue';
  import { Stats, OrbitControls } from '@tresjs/cientos';

  const torusRef = shallowRef();

  const { onLoop } = useRenderLoop();

  // onLoop(({ delta, elapsed }) => {
  //   if (torusRef.value) {
  //     torusRef.value.rotation.x += delta;
  //     torusRef.value.rotation.y += delta;

  //     // torusRef.value.position.x = Math.sin(elapsed * 2);

  //     // torusRef.value.scale.set(Math.sin(elapsed * 2), Math.sin(elapsed * 2), Math.sin(elapsed * 2));
  //   }
  // });

  // watchEffect(() => {
  //   console.log('torusRef', torusRef);
  // });
</script>
