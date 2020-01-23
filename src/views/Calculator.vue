<template>
  <div class="home">
    <h1>Calculator</h1>
    <div id="grid">
      <div class="calculator">
        <div class="answer">{{ this.answer }}</div>
        <div class="equation">
          <sui-input placeholder="0" v-model="formula" v-on:keyup.enter="evaluate()" />
        </div>
        <div class="rowOne">
          <sui-button color="blue" class="btn operator" content="AC" @click="clear()"></sui-button>
          <sui-button color="blue" class="btn operator" content="+/-" @click="sign()"></sui-button>
          <sui-button color="blue" class="btn operator" content="/" @click="append('/')"></sui-button>
          <sui-button color="blue" class="btn operator" content="⌫" @click="backspace()"></sui-button>
        </div>
        <div class="rowTwo">
          <sui-button color="blue" class="btn digit" content="7" @click="append('7')"></sui-button>
          <sui-button color="blue" class="btn digit" content="8" @click="append('8')"></sui-button>
          <sui-button color="blue" class="btn digit" content="9" @click="append('9')"></sui-button>
          <sui-button color="blue" class="btn operator" content="*" @click="append('*')"></sui-button>
        </div>
        <div class="rowThree">
          <sui-button color="blue" class="btn digit" content="4" @click="append('4')"></sui-button>
          <sui-button color="blue" class="btn digit" content="5" @click="append('5')"></sui-button>
          <sui-button color="blue" class="btn digit" content="6" @click="append('6')"></sui-button>
          <sui-button color="blue" class="btn operator" content="-" @click="append('-')"></sui-button>
        </div>
        <div class="rowFour">
          <sui-button color="blue" class="btn digit" content="1" @click="append('1')"></sui-button>
          <sui-button color="blue" class="btn digit" content="2" @click="append('2')"></sui-button>
          <sui-button color="blue" class="btn digit" content="3" @click="append('3')"></sui-button>
          <sui-button color="blue" class="btn operator" content="+" @click="append('+')"></sui-button>
        </div>
        <div class="rowFive">
          <sui-button color="blue" class="btn digit zero" content="0" @click="append('0')"></sui-button>
          <sui-button color="blue" class="btn" content="." @click="append('.')"></sui-button>
          <sui-button color="blue" class="btn operator" content="=" @click="evaluate()"></sui-button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formula: "",
      answer: ""
    };
  },
  methods: {
    /*
     * FUNCTION: evaluate()
     * PARAMETERS: none
     * FUNCTIONALITY: evaluate() was already written by instructors.
     */
    evaluate() {
      this.enterPressed = true;
      try {
        /* WARNING! Never use eval in production code. */
        // eslint-disable-next-line no-eval
        let result = eval(this.formula);
        let tmpStr = result.toString().slice(0, 10);
        result = Number(tmpStr);
        this.formulaAlert = false;
        this.answer = result;
      } catch (exception) {
        this.formulaAlert = true;
      }
    },

    /*
     * FUNCTION: append()
     * PARAMETERS: value: Value to be appended to end of string.
     * FUNCTIONALITY: append() first checks to see if this.formula has been set.
     * If not, then it just replaces the value. If it has been set, it adds the
     * user input string (the button pressed) to the end of this.formula.
     */
    append(value) {
      if (this.formula) {
        this.formula = this.formula + String(value);
      } else {
        this.formula = value;
      }
      console.log(value);
    },

    /*
     * FUNCTION: backspace()
     * PARAMETERS: none
     * FUNCTIONALITY: backspace() uses slice() to cut the last character off from
     * the string. It uses toString() to ensure that this.formula is a string
     * (otherwise this function would not work when deleting the last character
     * from a result).
     */
    backspace() {
      this.formula = this.formula.toString().slice(0, -1);
    },

    /*
     * FUNCTION: clear()
     * PARAMETERS: none
     * FUNCTIONALITY: clear() sets this.formula back to the empty string, clearing
     * all previous data, and ultimately clearing the calculator to a fresh start
     */
    clear() {
      this.formula = "";
      this.answer = "";
    },

    /*
     * FUNCTION: sign()
     * PARAMETERS: none
     * FUNCTIONALITY: sign() sets this.formula equal to a negative number if
     * pressed for first time. If pressed again, sets this.formula back to a
     * positive number.
     */
    sign() {
      if (this.formula != "") {
        if (this.formula.charAt(0) === "-") {
          this.formula = this.formula.slice(1);
        } else {
          let tmpInt = Number(this.formula) * -1;
          this.formula = tmpInt.toString();
        }
      }
    }
  }
};
</script>

<style>
body {
  background-image: linear-gradient(#f3c6ef, #ec7de2);
}
.calculator {
  padding: 6vh 0 12vh 0;
  background-color: #ffffff;
  border-radius: 15px;
  width: 24vw;
  margin: 0 auto;
}

h1 {
  color: #ffffff;
  padding-top: 50px;
  text-align: center;
}

.answer {
  font-weight: 700;
  color: #f03939;
  font-size: 30px;
  height: 15px;
  margin-bottom: 20px;
}

.equation {
  font-weight: 500;
  font-size: 20px;
  border-bottom: 1px solid #a5ab9f;
  width: 16vw;
  margin: 0 auto;
  height: 30px;
  display: flex;
  color: #f03939;
}

.ui.input > input {
  border: none;
  width: 15vw;
  color: #f03939;
}

.ui.input > input:focus {
  color: #f03939;
}

.ui.blue.button {
  width: 4vw;
  height: 4vw;
  padding: 0.8rem;
  font-size: 1.5rem;
  transition: 0.2s ease-in-out;
  line-height: 10px;
  background-color: #5bcb88;
  box-shadow: 0px 4px rgba(0, 0, 0, 0.3);
  margin-top: 5px;
}

.ui.blue.button:hover {
  background-color: #288b51;
}

.ui.blue.button:focus {
  background-color: #5bcb88;
}

.button.btn.digit.zero.ui.blue.button {
  flex: 0.51;
}

.button.btn.operator.ui.blue.button {
  padding: 0.6rem;
  vertical-align: middle;
  text-align: center;
  background-color: #a9d9fc;
}

.button.btn.operator.ui.blue.button:hover {
  transition: 0.2s ease-in-out;
  background-color: #3a7bb4;
}

.ui.blue.button:active {
  box-shadow: 0px 0px;
  transform: translateY(4px);
}

#grid {
  width: 30%;
  margin-left: auto;
  margin-right: auto;
  margin-top: 2vw;
  padding-bottom: 30px;
  padding-top: 10px;
}

.rowOne,
.rowTwo,
.rowThree,
.rowFour,
.rowFive {
  display: flex;
  flex-direction: row;
  justify-content: center;
  margin-top: 5px;
}

@media screen and (max-width: 950px) and (min-width: 600px) {
  #grid {
    width: 50%;
  }
  .calculator {
    padding: 10vh 6vw 10vh 6vw;
    background-color: #ffffff;
    border-radius: 15px;
    /* width: 32vw; */
    width: 65%;
  }

  .ui.blue.button {
    width: 5vw;
    height: 5vw;
    padding: 0.8rem;
    font-size: 1.2rem;
    transition: 0.2s ease-in-out;
    line-height: 10px;
  }

  .button.btn.digit.zero.ui.blue.button {
    flex: 1.6;
  }

  .button.btn.operator.ui.blue.button {
    padding: 0.5rem;
  }

  .equation {
    width: 16vw;
  }
}

@media screen and (max-width: 600px) {
  #grid {
    width: 50%;
  }
  .calculator {
    padding: 10vh 10vw 10vh 10vw;
    background-color: #ffffff;
    border-radius: 15px;
    width: 50vw;
  }

  .ui.blue.button {
    width: 3em;
    height: 3em;
    padding: 0.8rem;
    font-size: 1rem;
    transition: 0.2s ease-in-out;
    line-height: 10px;
  }

  .button.btn.digit.zero.ui.blue.button {
    flex: 1;
  }

  .button.btn.operator.ui.blue.button {
    padding: 0.5rem;
  }

  .equation {
    width: 25vw;
  }
}
</style>
