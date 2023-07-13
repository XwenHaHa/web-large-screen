<template>
  <div class="more-container">
    <z-row :gutter="12">
      <z-col :span="7">
        <div class="echartList">
          <div class="itemChart">
            <four-angel>
              <gauge-chart />
            </four-angel>
          </div>
          <div class="itemChart">
            <four-angel>
              <tree-chart />
            </four-angel>
          </div>
          <div class="itemChart">
            <four-angel>
              <radar-chart />
            </four-angel>
          </div>
        </div>
      </z-col>
      <z-col :span="10">
        <four-angel> </four-angel>
      </z-col>
      <z-col :span="7">
        <four-angel> </four-angel>
      </z-col>
    </z-row>
  </div>
</template>

<script>
import { ZRow, ZCol } from '@UI/components'
import fourAngel from '@/components/fourAngel/index'
import { gaugeChart, treeChart, radarChart } from './components'
export default {
  name: 'more',
  components: {
    ZRow,
    ZCol,
    fourAngel,
    gaugeChart,
    treeChart,
    radarChart
  }
}
</script>

<style lang="scss" scoped>
.more-container {
  width: 100%;
  height: 100%;
  position: relative;
  .echartList {
    width: 100%;
    height: 100%;
    display: flex;
    flex-wrap: wrap;
    align-content: space-between;

    .itemChart {
      height: 32.1%;
      width: 100%;
    }
  }
}
</style>
