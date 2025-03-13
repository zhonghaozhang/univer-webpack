<script setup lang="ts">
import {onMounted} from "vue";
import { createUniver, defaultTheme, LocaleType, merge } from '@univerjs/presets';
import { UniverSheetsCorePreset } from '@univerjs/presets/preset-sheets-core';
import UniverPresetSheetsCoreZhCN from '@univerjs/presets/preset-sheets-core/locales/zh-CN';
import {UniverSheetsConditionalFormattingPreset} from "@univerjs/presets/preset-sheets-conditional-formatting";
import sheetsConditionalFormattingZhCN from "@univerjs/presets/preset-sheets-conditional-formatting/locales/zh-CN";
import {UniverSheetsDataValidationPreset} from "@univerjs/presets/preset-sheets-data-validation";
import sheetsDataValidationZhCN from "@univerjs/presets/preset-sheets-data-validation/locales/zh-CN";
import {UniverSheetsDrawingPreset} from "@univerjs/presets/preset-sheets-drawing";
import sheetsDrawingZhCN from "@univerjs/presets/preset-sheets-drawing/locales/zh-CN";
import {UniverSheetsFilterPreset} from "@univerjs/presets/preset-sheets-filter";
import UniverPresetSheetsFilterZhCN from "@univerjs/presets/preset-sheets-filter/locales/zh-CN";
import {UniverSheetsHyperLinkPreset} from "@univerjs/presets/preset-sheets-hyper-link";
import sheetsHyperLinkZhCN from "@univerjs/presets/preset-sheets-hyper-link/locales/zh-CN";
import {UniverSheetsFindReplacePreset} from "@univerjs/presets/preset-sheets-find-replace";
import UniverPresetSheetsFindReplaceZhCN from "@univerjs/presets/preset-sheets-find-replace/locales/zh-CN";

import {UniverSheetsCrosshairHighlightPlugin} from '@univerjs/sheets-crosshair-highlight';
import SheetsCrosshairHighlightZhCN from '@univerjs/sheets-crosshair-highlight/locale/zh-CN';

import "@univerjs/presets/lib/styles/preset-sheets-core.css";
import "@univerjs/presets/lib/styles/preset-sheets-conditional-formatting.css";
import "@univerjs/presets/lib/styles/preset-sheets-data-validation.css";
import "@univerjs/presets/lib/styles/preset-sheets-drawing.css";
import "@univerjs/presets/lib/styles/preset-sheets-filter.css";
import "@univerjs/presets/lib/styles/preset-sheets-hyper-link.css";
import '@univerjs/sheets-crosshair-highlight/lib/index.css';

import '@univerjs/sheets-crosshair-highlight/facade';
onMounted(() => {
  const { univer, univerAPI } = createUniver({
    locale: LocaleType.ZH_CN,
    locales: {
      [LocaleType.ZH_CN]: merge(
          {},
          UniverPresetSheetsCoreZhCN,
          sheetsConditionalFormattingZhCN,
          sheetsDataValidationZhCN,
          sheetsDrawingZhCN,
          sheetsHyperLinkZhCN,
          UniverPresetSheetsFilterZhCN,
          UniverPresetSheetsFindReplaceZhCN,
          SheetsCrosshairHighlightZhCN
      ),
    },
    theme: defaultTheme,
    presets: [
      UniverSheetsCorePreset({
        container: 'Edit',
      }),
      UniverSheetsFilterPreset(),
      UniverSheetsConditionalFormattingPreset(),
      UniverSheetsDataValidationPreset(),
      UniverSheetsDrawingPreset(),
      UniverSheetsHyperLinkPreset(),
      UniverSheetsFindReplacePreset(),
    ],
  });

  univerAPI.createWorkbook({ name: 'Test Sheet' });
})

</script>

<template>
  <div id="Edit"></div>
</template>

<style scoped>
#Edit{
  height: 100%;
  width: 100%;
}
</style>
