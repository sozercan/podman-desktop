<script lang="ts">
import WindowControlButton from './ControlButton.svelte';

export let platform: string;

async function minimize(): Promise<void> {
  return window.windowMinimize();
}

async function maximize(): Promise<void> {
  return window.windowMaximize();
}

async function close(): Promise<void> {
  return window.windowClose();
}
</script>

<!-- Display the min, max and close buttons and avoid drag & drop on this region-->
<div
  class="absolute {platform === 'linux' ? 'top-[7px] right-3' : ''} {platform === 'win32' ? 'top-0 right-0' : ''}"
  style="-webkit-app-region: none;">
  <div class="flex flex-row {platform === 'linux' ? 'space-x-2' : 'space-x-[1px]'}">
    <WindowControlButton platform={platform} name="Minimize" action={minimize} />
    <WindowControlButton platform={platform} name="Maximize" action={maximize} />
    <WindowControlButton platform={platform} name="Close" action={close} />
  </div>
</div>
