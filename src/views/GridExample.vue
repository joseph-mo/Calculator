<!--<template>
    <h1>Calculator</h1>
    <div class="container">
      <div class="rowOne">
        <sui-button class="firstRow" @click="append('AC')">AC</sui-button>
        <sui-button class="firstRow">+/-</sui-button>
        <sui-button class="firstRow">%</sui-button>
        <sui-button class="firstRow">/</sui-button>
      </div>
      <div class="rowTwo">
        <sui-button class="secondRow">7</sui-button>
        <sui-button class="secondRow">8</sui-button>
        <sui-button class="secondRow">9</sui-button>
        <sui-button class="secondRow">x</sui-button>
      </div>
      <div class="rowThree">
        <sui-button class="thirdRow">4</sui-button>
        <sui-button class="thirdRow">5</sui-button>
        <sui-button class="thirdRow">6</sui-button>
        <sui-button class="thirdRow">-</sui-button>
      </div>
      <div class="rowFour">
        <sui-button class="fourthRow">1</sui-button>
        <sui-button class="fourthRow">2</sui-button>
        <sui-button class="fourthRow">3</sui-button>
        <sui-button class="fourthRow">+</sui-button>
      </div>
      <div class="rowFive">
        <sui-button class="fifthRowZero">0</sui-button>
        <sui-button class="fifthRowDecimal">.</sui-button>
        <sui-button class="fifthRowEnter">=</sui-button>
      </div>
    </div>
  </div>
</template>-->


<template>
  <div id="grid">
    <h1>Semantic UI Grid Example</h1>
    <sui-grid :columns="2">
      <sui-grid-column>
        <sui-segment>Movie</sui-segment>
        <sui-segment>Toy Story 2</sui-segment>
        <sui-segment>Toy Story 3</sui-segment>
        <sui-segment>Toy Story 4</sui-segment>
      </sui-grid-column>
      <sui-grid-column>
        <sui-segment>Review</sui-segment>
        <sui-segment>
          <sui-rating :rating="value" :max-rating="5" />
        </sui-segment>
        <sui-segment>
          <sui-rating :rating="value" :max-rating="5" />
        </sui-segment>
        <sui-segment>
          <sui-rating :rating="value" :max-rating="5" />
        </sui-segment>
      </sui-grid-column>
    </sui-grid>
  </div>
</template>

    <!-- <sui-grid>
      <sui-grid-row>
        <sui-grid-column width="twelve">
          <sui-segment>this is a long sentence.</sui-segment>
        </sui-grid-column>
        <sui-grid-column width="four">
          <sui-segment>word</sui-segment>
        </sui-grid-column>
      </sui-grid-row>
      <sui-grid-column width="four">
        <sui-segment>element 3</sui-segment>
      </sui-grid-column>
      <sui-grid-column width="four">
        <sui-segment>element 4</sui-segment>
      </sui-grid-column>
      <sui-grid-column width="four">
        <sui-segment>element 5</sui-segment>
      </sui-grid-column>
      <sui-grid-column width="four">
        <sui-segment>element 6</sui-segment>
      </sui-grid-column>
      <sui-grid-column width="four">
        <sui-segment>element 7</sui-segment>
      </sui-grid-column>
    </sui-grid>-->


<style>
#grid {
  width: 50%;
  margin-left: auto;
  margin-right: auto;
  margin-top: 5vw;
}

.rowOne,
.rowTwo,
.rowThree,
.rowFour,
.rowFive {
  display: flex;
  flex-direction: row;
  justify-content: center;
  margin-top: 30px;
}

.firstRow,
.secondRow,
.thirdRow,
.fourthRow,
.fifthRowDecimal,
.fifthRowZero {
  flex: 0.1;
}

.fifthRowEnter {
  flex: 0.4;
}
</style>
