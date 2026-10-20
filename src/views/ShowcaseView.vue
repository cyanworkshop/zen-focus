<template>
  <div class="showcase-view">
    <el-tabs type="border-card">
      <el-tab-pane label="聯絡資訊">
        <el-descriptions border :label-width="180" size="small" :column="1">
          <el-descriptions-item>
            <template #label>
              <div class="cell-item">
                官方商務聯絡<br />
                Business Inquiry
              </div>
            </template>
            <a
              href="mailto:cyanworkshop.official@gmail.com"
              title="cyanworkshop.official@gmail.com"
              target="_blank"
              rel="noopener noreferrer"
            >
              cyanworkshop.official@gmail.com
            </a>
            <br />
            來信後約1-3個工作天回覆。
          </el-descriptions-item>
          <el-descriptions-item>
            <template #label>
              <div class="cell-item">
                官方網站<br />
                Official Website
              </div>
            </template>
            <a
              href="https://cyanworkshop.com"
              title="https://cyanworkshop.com"
              target="_blank"
              rel="noopener noreferrer"
            >
              https://cyanworkshop.com ↗
            </a>
          </el-descriptions-item>
          <el-descriptions-item>
            <template #label>
              <div class="cell-item">
                GitHub 官方組織<br />
                GitHub Organization
              </div>
            </template>
            <a
              href="https://github.com/cyanworkshop"
              title="https://github.com/cyanworkshop"
              target="_blank"
              rel="noopener noreferrer"
            >
              https://github.com/cyanworkshop ↗
            </a>
          </el-descriptions-item>
          <el-descriptions-item>
            <template #label>
              <div class="cell-item">
                服務範疇與詢價說明<br />
                Service Scope & Pricing
              </div>
            </template>
            <h4 class="my-2">【服務內容】</h4>
            <b>前端架構優化</b>：Vue 3 / TypeScript 企業級系統開發與效能調優。
            <br />
            <b>UI/UX 設計系統</b>：Tailwind CSS / SCSS 模組化設計系統組建。
            <br />
            <b>資安與 DOM 調試</b>：深度前端資安防護與效能瓶頸排查。
            <br />
            <h4 class="my-2">
              <a
                href="https://cyanworkshop.com/contact/"
                title="https://cyanworkshop.com/contact/"
                target="_blank"
                rel="noopener noreferrer"
              >
                立即詢價↗
              </a>
            </h4>
          </el-descriptions-item>
        </el-descriptions>
      </el-tab-pane>
      <el-tab-pane label="開發技術">
        <el-table :data="tableData" border>
          <el-table-column
            v-for="col in tableColumn"
            :key="col.name"
            :prop="col.name"
            :label="col.title"
            :width="col.width"
          />
        </el-table>
      </el-tab-pane>
      <el-tab-pane label="風格展示">
        <div class="flex items-center justify-start mb-2 gap-10">
          <h3>Button Status</h3>
          <el-radio-group v-model="showType">
            <el-radio
              v-for="item in showTypeOptions"
              :key="item.value"
              :value="item.value"
              size="large"
            >
              {{ item.label }}
            </el-radio>
          </el-radio-group>
        </div>

        <hr class="mb-4" />

        <h3>{{ showType }}</h3>

        <div class="button-row">
          <el-button
            v-for="t in formattedButtons"
            :key="t.type"
            :type="t.type"
            circle
            :icon="Star"
            :disabled="showType === 'Disabled'"
            :loading="showType === 'Loading'"
          >
          </el-button>
        </div>
        <div class="button-row">
          <el-button
            v-for="t in formattedButtons"
            :key="t.type"
            :type="t.type"
            :disabled="showType === 'Disabled'"
            :loading="showType === 'Loading'"
          >
            {{ t.label }}
          </el-button>
        </div>
        <div class="button-row">
          <el-button
            v-for="t in formattedButtons"
            :key="t.type"
            :type="t.type"
            plain
            :disabled="showType === 'Disabled'"
            :loading="showType === 'Loading'"
          >
            {{ t.label }}
          </el-button>
        </div>
        <div class="button-row">
          <el-button
            v-for="t in formattedButtons"
            :key="t.type"
            :type="t.type"
            dashed
            :disabled="showType === 'Disabled'"
            :loading="showType === 'Loading'"
          >
            {{ t.label }}
          </el-button>
        </div>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script setup lang="ts">
import { Star } from "@element-plus/icons-vue";
import { ref, computed } from "vue";
const tableColumn = computed(() => [
  {
    name: "type",
    title: "功能分類",
    width: 180,
  },
  {
    name: "tool",
    title: "使用工具 / 技術",
  },
]);
const tableData = computed(() => [
  {
    type: "程式碼編輯器",
    tool: "Cursor",
  },
  {
    type: "前端框架主架構",
    tool: "Vue 3 + Vite + TypeScript",
  },
  {
    type: "全域狀態管理",
    tool: "Pinia",
  },
  {
    type: "語系切換管理",
    tool: "i18n",
  },
  {
    type: "版本控制",
    tool: "Git / GitHub",
  },
  {
    type: "CSS & UI 框架",
    tool: "SASS + Tailwind.css + Element Plus",
  },
  {
    type: "部署與上架",
    tool: "Vercel + GitHub",
  },
]);

// 按鈕風格展示
const showType = ref("Normal");
const showTypeOptions = [
  {
    value: "Normal",
    label: "Normal",
  },
  {
    value: "Disabled",
    label: "Disabled",
  },
  {
    value: "Loading",
    label: "Loading",
  },
];
const buttonList = [
  "default",
  "primary",
  "success",
  "warning",
  "danger",
  "info",
];
const formattedButtons = computed(() =>
  buttonList.map((t) => ({
    type: t,
    label: t.charAt(0).toUpperCase() + t.slice(1),
  })),
);
</script>

<style lang="scss">
.button-row {
  margin: 10px 0;
}
</style>
