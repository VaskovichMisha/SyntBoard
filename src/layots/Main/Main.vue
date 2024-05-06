<template>
  <div class="_container">
    <h1 class="logo">
      <img src="@/assets/image/logo.png" alt="">
      <span>SyntBoard</span>
    </h1>
    <div class="main">
      <div class="main__left">
        <div class="main__data">
          <div class="main__data-title">Data</div>
          <div class="main__data-container">
            <div class="main__data-block">
              <span>Fmri1.mat</span>
              <span>Fmri2.mat</span>
            </div>
            <div class="main__data-buttons">
              <div class="main__data-file">
                <label for="file">Upload</label>
                <input type="file" id="file"/>
              </div>
              <Button
                  text="Clear"
                  color="blue"
              />
              <Button
                  text="View"
                  color="blue"
              />
            </div>
          </div>
        </div>
        <div class="main__data-graph">
          <Tabs
              :tabs="tabs"
              @change-tab="changeImage"
          />
          <div class="main__data-graph-block">
            <img v-if="numberImage === 0" src="@/assets/image/graph.png" alt="">
            <img v-if="numberImage === 1" src="@/assets/image/heatmap.png" alt="">
            <img v-if="numberImage === 2" src="@/assets/image/brain.png" alt="">
          </div>
        </div>
      </div>
      <div class="main__right">
        <div class="main__tuning">
          <div class="main__tuning-title">Tuning</div>
          <div class="main__tuning-radios">
            <Radio
                v-for="radio in radios"
                :radio="radio"
                name="radio-tuning"
            />
          </div>
          <div class="main__tuning-selects">
            <div class="main__tuning-select">
              <span>Architecture</span>
              <Select
                  :selectData="selectArchitecture"
                  selected="Selected Architecture"
              />
            </div>
            <div class="main__tuning-select">
              <span>Domain adaptation</span>
              <Select
                  :selectData="selectDomainAdaptation"
                  selected="Selected Domain Adaptation"
              />
            </div>
            <div class="main__tuning-select">
              <span>Hyperparameters</span>
              <Select
                  :selectData="selectHyperparameters"
                  selected="Selected Hyperparameters"
              />
            </div>
            <div class="main__tuning-select">
              <span>Features</span>
              <Select
                  :selectData="selectFeatures"
                  selected="Selected Features"
              />
            </div>
          </div>
          <Button
              text="Calculate"
              color="white"
          />
        </div>
        <div class="main__value">
          <div class="main__value-table">
            <div></div>
            <div class="table__up">
              <span>Actual Value</span>
              <div>
                <span>Positive</span>
                <span>Negative</span>
              </div>
            </div>
            <div class="table__right">
              <span>Predicated Value</span>
              <div>
                <span>Positive</span>
                <span>Negative</span>
              </div>
            </div>
            <div class="table__data">
              <div>
                <span>25</span>
              </div>
              <div class="">
                <span>15</span>
              </div>
              <div class="">
                <span>12</span>
              </div>
              <div class="">
                <span>45</span>
              </div>
            </div>
          </div>
          <div class="main__value-data">
            <div class="main__value-data-item">
              <span>Accuracy</span>
              <span>78%</span>
            </div>
            <div class="main__value-data-item">
              <span>Precision</span>
              <span>76%</span>
            </div>
            <div class="main__value-data-item">
              <span>Recall</span>
              <span>67%</span>
            </div>
            <div class="main__value-data-item">
              <span>F-1 score</span>
              <span>71%</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Button from "@/components/UI/Button/Button.vue";
import Tabs from "@/components/UI/Tabs/Tabs.vue";
import Radio from "@/components/UI/Radio/Radio.vue";
import Select from "@/components/UI/Select/Select.vue";

export default {
  data() {
    return {
      tabs: [
        { title: 'Graph', id: 0},
        { title: 'Heatmap', id: 1},
        { title: 'Brain Image', id: 2},
      ],
      radios: [
        { label: 'Manual', id: 0 },
        { label: 'Auto', id: 1 },
      ],
      selectArchitecture: [
        { text: 'BrainNetCNN', id: 0 },
        { text: 'FBNetGNN', id: 1 },
        { text: 'BrainNetworkTransformer', id: 2 },
        { text: 'Ensemble', id: 3 },
        { text: 'KNeighborsClassifier', id: 4 },
        { text: 'LinearSVC', id: 5 },
        { text: 'RandomForest', id: 6 },
        { text: 'DecisionTreeClassifier', id: 7 },
        { text: 'GCN', id: 8 },
      ],
      selectDomainAdaptation: [
        { text: 'MoE', id: 0 },
        { text: 'Align', id: 1 },
        { text: 'Shallow DA', id: 2 },
        { text: 'Deep DA', id: 3 },
        { text: 'Supervised DA', id: 4 },
        { text: 'Multimodality DA', id: 5 },
      ],
      selectHyperparameters: [
        { text: 'lyers n', id: 0 },
        { text: 'batchsize', id: 1 },
        { text: 'shuffle', id: 2 },
        { text: 'optimizer', id: 3 },
        { text: 'epochs', id: 4 },
      ],
      selectFeatures: [
        { text: 'Features 1', id: 0 },
        { text: 'Features 2', id: 1 },
        { text: 'Features 3', id: 2 },
      ],
      numberImage: 0
    }
  },
  components: {
    Select,
    Radio,
    Tabs,
    Button,
  },
  methods: {
    changeImage(id) {
      this.numberImage = id
    }
  }
}
</script>

<style lang="scss" scoped>
@import "main";
</style>