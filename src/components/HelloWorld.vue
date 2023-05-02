<template>
  <div class="main">
    <div class="test-box">
      <div class="body-container">
        <div class="title">Тестовое задание</div>
        <div
          v-for="(word, index) in words"
          :key="index"
          :class="{ highlight: currentIndex === index, word: true }"
        >
          &nbsp;{{ word }}
        </div>
        <div class="btn" @click.once="highlightWords">Обработать</div>
      </div>
      <div class="man">
        <img src="../assets/Brain.svg" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      text: "Тестовое задание — отличный инструмент оценки навыков. Без него бывает сложно понять, насколько соискатель подходит компании. Выбрать кандидата только по резюме и портфолио трудно, ведь они не всегда отражают опыт и скиллы соискателя.",
      currentIndex: -1,
    };
  },
  computed: {
    words: function () {
      return this.text.split(" ");
    },
  },
  methods: {
    highlightWords() {
      setInterval(() => {
        do {
          this.currentIndex = (this.currentIndex + 1) % this.words.length;
        } while (this.words[this.currentIndex].includes("—"));
      }, 1000);
    },
  },
};
</script>

<style>
.title {
  font-family: "Open Sans";
  font-style: normal;
  font-weight: 300;
  font-size: 24px;
  line-height: 34px;
  color: #ffffff;
  margin-bottom: 7px;
}

.word {
  display: inline-block;
  font-family: "Open Sans";
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 22px;
  color: rgba(255, 255, 255, 0.7);
}

.highlight {
  color: black;
}

.main {
  width: 620px;
  height: 290px;
  background: #e7832b;
  border-radius: 12px;
  display: inline-block;
}

.test-box {
  display: flex;
  height: 100%;
}

.body-container {
  text-align: initial;
  margin: 26px 26px 32px 39px;
  width: 341px;
  height: 232px;
}

.btn {
  display: flex;
  font-family: "Open Sans";
  font-style: normal;
  font-weight: 700;
  font-size: 16px;
  line-height: 24px;
  text-align: center;
  letter-spacing: 1px;
  text-transform: uppercase;
  color: #000000;
  width: 341px;
  height: 52px;
  background: #fab42a;
  border-radius: 4px;
  align-items: center;
  justify-content: space-around;
  margin-top: 7px;
  cursor: pointer;
}
.btn:hover {
  box-shadow: -1px 0px 5px 0px #f4e538;
}

.man {
  width: 100%;
  display: flex;
  align-items: flex-end;
  height: 100%;
  justify-content: space-around;
}

@media only screen and (min-device-width: 375px) and (max-device-width: 1024px) and (orientation: portrait) {
  .main {
    width: 348px;
    height: 505px;
  }
  .body-container {
    margin: 34px 34px 47px 32px;
    width: 307px;
    height: 242px;
    text-align: center;
  }
  .btn {
    width: 307px;
    height: 52px;
  }
  .test-box {
    flex-direction: column;
    align-items: center;
  }
  .man {
    align-items: baseline;
    height: 100%;
    overflow: hidden;
  }
  .title {
    line-height: 30px;
    margin-bottom: 14px;
  }
}
</style>
