<template>
  <menu-bar>
    <template #left-menu>
      <router-link :to="{ name: 'logs' }" tag="li">
        <icon-arrow-back/>
      </router-link>
      <li>Edit Log</li>
    </template>
    <template #right-menu>
      <a
        v-if="logs[currentLogIndex] && logs[currentLogIndex].remoteUri"
        :href="logs[currentLogIndex].remoteUri">
        <li>
          <icon-open-in-new/>
        </li>
      </a>
      <li @click="$emit('deleteCurrentLog')">
        <icon-delete/>
      </li>
    </template>
    <template #more-menu>
      <a
        v-if="logs[currentLogIndex].remoteUri !==''"
        :href="logs[currentLogIndex].remoteUri">
        <li>Open in browser</li>
      </a>
      <li @click="$emit('deleteCurrentLog')">
        Delete from device
      </li>
    </template>
  </menu-bar>
</template>

<script>
import MenuBar from './MenuBar.vue'; // eslint-disable-line import/extensions
import IconArrowBack from '../../icons/icon-arrow-back.vue'; // eslint-disable-line import/extensions
import IconDelete from '../../icons/icon-delete.vue'; // eslint-disable-line import/extensions
import IconOpenInNew from '../../icons/icon-open-in-new.vue'; // eslint-disable-line import/extensions

export default {
  name: 'EditLogsMenuBar',
  components: { MenuBar, IconArrowBack, IconDelete, IconOpenInNew },
  props: [ 'logs', 'currentLogIndex' ],
};
</script>
