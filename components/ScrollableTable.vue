<script setup lang="ts">
const props = defineProps<{
    maxHeight?: string
    stickyHeader?: boolean
}>()
</script>

<template>
    <div class="slidev-scroll-table" :class="{ 'sticky-header': props.stickyHeader }"
        :style="{ maxHeight: props.maxHeight ?? '360px' }">
        <slot />
    </div>
</template>

<style scoped>
.slidev-scroll-table {
    overflow-y: auto;
    border: 1px solid var(--slidev-border-color, #ddd);
    border-radius: 6px;
}

/* table base */
:deep(table) {
    width: 100%;
    border-collapse: collapse;
}

:deep(td) {
    padding: 0.4rem 0.6rem;
    border-bottom: 1px solid #e5e5e5;
    text-align: left;
    vertical-align: top;
}

/* 表头单元格：不使用 border */
:deep(th) {
    padding: 0.4rem 0.6rem;
    border-bottom: 1px solid #e5e5e5;
    text-align: left;
    vertical-align: top;
}

/* sticky header */
.slidev-scroll-table.sticky-header :deep(thead th) {
    position: sticky;
    top: 0;
    z-index: 10;

    /* 非透明背景，防止内容穿透 */
    background-color: var(--slidev-code-background, #ffffff);

    /* 视觉增强（可选） */
    box-shadow: 0 1px 0 rgba(0, 0, 0, 0.08);
}
</style>