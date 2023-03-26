<template>
  <c-avatar>
    <c-avatar-badge bg="red.500" />
  </c-avatar>
</template>

<script setup lang="ts">
import {
  chakra,
  useColorMode,
  useColorModeValue,
  useTheme,
  CStack,
  CHeading,
  CWrap,
  CWrapItem,
  CCircle,
  CBadge,
  CButtonGroup,
  CButton,
  CIconButton,
  CAvatar,
  CAvatarBadge,
} from '@chakra-ui/vue-next';
import { useStorage } from '@vueuse/core';
import DocumentationIcon from './components/icons/documentation-icon';
import ExternalLinkIcon from './components/icons/external-link';
import DiscordIcon from './components/icons/discord-icon';
import NuxtLogo from './components/icons/nuxt-logo';

const { toggleColorMode } = useColorMode();

const themeConfig = {
  color: 'whatsapp',
};
const selectedColor = useStorage('theme.color', themeConfig);

const theme = useTheme();

const colors = computed(
  () =>
    new Set(
      Object.keys(theme.colors!)
        .filter((color) => typeof theme.colors![color] === 'object')
        .filter((color) => !['blackAlpha', 'whiteAlpha'].includes(color))
    )
);

function changeColorMode() {
  toggleColorMode();
}
</script>
