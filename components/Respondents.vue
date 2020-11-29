<template>
  <div class="respondents">
    <h2 class="respondents__header">Добавить опрос</h2>
    <div class="respondents__rules">
      <div
        v-for="(rule, index) in rules"
        :key="index"
        class="respondents__rule"
      >
        <div class="respondents__row">
          <div class="respondents__condition respondents__condition-label">
            Условие {{ index + 1 }}
          </div>
          <div class="respondents__condition">
            <label>
              <select
                class="respondents__select respondents__select_margin-bottom"
                v-model="rule.type"
              >
                <option value="">Выберите условие</option>
                <option
                  v-for="(ruleType, type) in ruleTypes"
                  :key="type"
                  :value="type"
                >
                  {{ ruleType.name }}
                </option>
              </select>
            </label>
          </div>
        </div>
        <template v-if="rule.type">
          <div
            v-for="(arg, argIndex) in rule.arguments"
            :key="argIndex"
            class="respondents__row"
          >
            <div class="respondents__condition respondents__condition-label">
              <span v-if="argIndex" class="respondents__logic">или</span>
              {{ ruleTypes[rule.type].entityName }} {{ argIndex + 1 }}
            </div>
            <div class="respondents__condition">
              <template v-if="rule.type === 'age'">
                от
                <label
                  ><input
                    v-model="arg.from"
                    type="number"
                    class="respondents__input"
                /></label>
                до
                <label
                  ><input
                    v-model="arg.to"
                    type="number"
                    class="respondents__input"
                /></label>
              </template>
              <template v-else>
                <label>
                  <select
                    class="respondents__select respondents__select_status"
                    v-model="arg.value"
                  >
                    <option
                      v-for="(option, optindex) in ruleTypes[rule.type].options"
                      :key="optindex"
                      :value="option.value"
                    >
                      {{ option.label }}
                    </option>
                  </select>
                </label>
              </template>
            </div>
          </div>
        </template>
        <div class="respondents__row">
          <div class="respondents__condition respondents__condition-label" />
          <div class="respondents__condition respondents__condition-buttons">
            <button
              class="respondents__button respondents__button-delete"
              @click="deleteRule(rule)"
            >
              <i class="gg-trash"></i>
              Удалить условие
            </button>
            <button
              v-if="rule.type"
              class="respondents__button respondents__button-add"
              @click="addRuleArgument(rule)"
            >
              + Добавить {{ ruleTypes[rule.type].entityName }}
            </button>
          </div>
        </div>
      </div>
    </div>
    <div class="respondents__add">
      <button class="respondents__add-button" @click="addRule">
        <span class="respondents__add-span">+</span>
        <span class="respondents__add-text">
          Нажмите, чтобы добавить новое условие выборки. Все условия связываются
          между собой логическим «И»
        </span>
      </button>
    </div>
    <div class="footer">
      <button class="respondents__button footer__button-test">
        Протестировать опрос
      </button>
      <button class="respondents__button footer__button-next">Далее →</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PollRespondents',
  props: {
    rules: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      ruleTypes: {
        age: {
          name: 'Возраст респондента',
          entityName: 'диапазон',
        },
        cardType: {
          name: 'Тип карты лояльности',
          entityName: 'тип',
          options: [
            {
              value: 'silver',
              label: 'Silver',
            },
            {
              value: 'gold',
              label: 'Gold',
            },
            {
              value: 'platinum',
              label: 'Platinum',
            },
          ],
        },
        cardStatus: {
          name: 'Статус карты лояльности',
          entityName: 'статус',
          options: [
            {
              value: 'active',
              label: 'Активна',
            },
            {
              value: 'inactive',
              label: 'Не активна',
            },
          ],
        },
      },
    };
  },
  methods: {
    addRule() {
      this.rules.push({
        type: '',
        arguments: [],
      });
    },
    addRuleArgument(rule) {
      const argument =
        rule.type === 'age'
          ? {
              from: '',
              to: '',
            }
          : {
              value: this.ruleTypes[rule.type].options[0].value,
            };
      rule.arguments.push(argument);
    },
    deleteRule(rule) {
      this.$delete(this.rules, this.rules.indexOf(rule));
    },
  },
};
</script>

<style scoped>
.respondents {
  box-shadow: 0 8px 15px #dedede;
}

.respondents__header {
  padding: 18px 0 18px 38px;
  color: #ccc;
  font-weight: bold;
  font-size: 16px;
  display: block;
}

.respondents__rule {
  padding: 16px 37px;
  border-bottom: 1px solid #f1f1f1;
  position: relative;
}

.respondents__rule:nth-child(odd) {
  background-color: #fffcf6;
}

.respondents__rule:nth-child(even) {
  background-color: #f8faff;
}

.respondents__row {
  display: flex;
  margin-bottom: 16px;
}

.respondents__condition:last-child {
  flex-grow: 1;
}

.respondents__condition-label {
  width: 28%;
  text-transform: capitalize;
}

.respondents__select {
  width: 100%;
  height: 38px;
  background-color: #fff;
  border-radius: 6px;
  border: 2px solid #d3d3d3;
  outline: none;
  cursor: pointer;
  transition: 0.2s;
}

.respondents__select_margin-bottom {
  margin-bottom: 15px;
}

.respondents__select_status {
  width: 85%;
}

.respondents__logic {
  display: inline-block;
  background-color: #efefef;
  text-transform: lowercase;
  padding: 6px 10px 10px;
  border-radius: 5px;
  margin-right: 5px;
}

.respondents__input {
  height: 38px;
  width: 20%;
  background-color: #fff;
  border: 2px solid #d3d3d3;
  border-radius: 5px;
  outline: none;
}

.respondents__condition-buttons {
  display: flex;
  flex-direction: row-reverse;
  justify-content: space-between;
  margin-top: 20px;
}

.respondents__button-delete {
  border: 2px solid #f96d6d;
  color: #ee3131;
  transition: 0.2s;
  display: flex;
  flex-direction: row;
  align-items: center;
}

.gg-trash {
  margin-right: 12px;
}

.respondents__button {
  padding: 10px;
  border-radius: 8px;
  cursor: pointer;
  outline: none;
  background-color: transparent;
  font-weight: bold;
}

.respondents__button:hover {
  background-color: #f1f1f1;
}

.respondents__button-add {
  border: 2px solid #7ac17a;
  color: #7ac17a;
  transition: 0.2s;
}

.respondents__add-button {
  display: flex;
  justify-content: center;
  flex-direction: column;
  align-items: center;
  width: 740px;
  height: 100px;
  margin: 35px 37px 35px 37px;
  border-radius: 8px;
  border: 2px solid #f1f1f1;
  background: transparent;
  color: #4c9b5d;
  cursor: pointer;
}

.respondents__add-button:hover {
  background-color: #f1f1f1;
}

.respondents__add-text {
  max-width: 343px;
}

.respondents__add-span {
  font-size: 42px;
  line-height: 30px;
  display: block;
}

.footer {
  padding: 20px 37px;
  display: flex;
  justify-content: space-between;
  background-color: #ecfaec;
}

.footer__button-next {
  border: none;
  background-color: #18a436;
  color: #fff;
  padding: 13px 15px;
}

.footer__button-next:hover {
  background-color: #1ec141;
}

.footer__button-test {
  background-color: #fff;
  color: #4c9b5d;
  border: none;
  padding: 13px 15px;
}
</style>
