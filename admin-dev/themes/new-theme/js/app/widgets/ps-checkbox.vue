<!--**
 * Copyright since 2007 PrestaShop SA and Contributors
 * PrestaShop is an International Registered Trademark & Property of PrestaShop SA
 *
 * NOTICE OF LICENSE
 *
 * This source file is subject to the Open Software License (OSL 3.0)
 * that is bundled with this package in the file LICENSE.md.
 * It is also available through the world-wide-web at this URL:
 * https://opensource.org/licenses/OSL-3.0
 * If you did not receive a copy of the license and are unable to
 * obtain it through the world-wide-web, please send an email
 * to license@prestashop.com so we can send you a copy immediately.
 *
 * DISCLAIMER
 *
 * Do not edit or add to this file if you wish to upgrade PrestaShop to newer
 * versions in the future. If you wish to customize PrestaShop for your
 * needs please refer to https://devdocs.prestashop.com/ for more information.
 *
 * @author    PrestaShop SA and Contributors <contact@prestashop.com>
 * @copyright Since 2007 PrestaShop SA and Contributors
 * @license   https://opensource.org/licenses/OSL-3.0 Open Software License (OSL 3.0)
 *-->
<template>
  <div class="md-checkbox">
    <label>
      <input
        type="checkbox"
        :id="id"
        v-model="checked"
        :class="{'indeterminate' : isIndeterminate }"
      >
      <i class="md-checkbox-control" />
      <slot name="label" />
    </label>
  </div>
</template>

<script lang="ts">
  import Vue from 'vue';

  export default Vue.extend({
    props: {
      id: {
        type: String,
        required: false,
        default: '',
      },
      model: {
        type: Object,
        required: false,
        default: () => ({}),
      },
      isIndeterminate: {
        type: Boolean,
        required: false,
        default: false,
      },
    },
    watch: {
      checked(val: boolean): void {
        this.$emit('checked', {
          checked: val,
          item: this.model,
        });
      },
    },
    data() {
      return {
        checked: false,
      };
    },
  });
</script>
