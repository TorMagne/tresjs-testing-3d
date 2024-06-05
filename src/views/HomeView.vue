<template>
  <TresCanvas clear-color="#82DBC5" window-size>
    <Stats />
    <TresPerspectiveCamera />
    <TresMesh :position="[0, 0, 0]" ref="cubeRef">
      <TresBoxGeometry />
      <TresMeshNormalMaterial />
    </TresMesh>

    <!-- <TresAxesHelper /> -->
  </TresCanvas>
</template>

<script setup>
  import { useRenderLoop, useTres } from '@tresjs/core';
  import { shallowRef, watchEffect } from 'vue';
  import { Stats } from '@tresjs/cientos';

  const cubeRef = shallowRef();

  const { onLoop } = useRenderLoop();

  onLoop(({ delta, elapsed }) => {
    if (cubeRef.value) {
      cubeRef.value.rotation.x += delta;
      cubeRef.value.rotation.y = elapsed;

      cubeRef.value.position.x = Math.sin(elapsed * 2);

      cubeRef.value.scale.set(Math.sin(elapsed * 2), Math.sin(elapsed * 2), Math.sin(elapsed * 2));
    }
  });

  // watchEffect(() => {
  //   console.log('cubeRef', cubeRef);
  // });
</script>
