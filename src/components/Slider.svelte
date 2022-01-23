<script>
  let value = 16;
  let max = 75;
  let min = 16;
  let rStyle = "";

  const setNumberPosition = () => {
    const newValue = Number(((value - min) * 100) / (max - min));
    const newPosition = 10 - newValue * 0.2;
    console.log(newValue);
    console.log(newPosition);
    rStyle = `calc(${newValue}% + (${newPosition}px))`;
  };
</script>

<div class="slidecontainer">
  <div class="range-wrap">
    <div class="range-value" id="rangeV" style={"left: " + rStyle}>
      {value}
    </div>
    <input
      bind:value
      on:input={setNumberPosition}
      id="range"
      type="range"
      list="tickmarks"
      min="16"
      max="75"
      class="slider"
    />
  </div>
</div>

<style lang="scss">
  @use "../styles/" as *;

  .number {
    text-align: center;
    font-size: $font-size-l;
    font-weight: bold;
    margin-bottom: 20px;
  }

  input[type="range"] {
    -webkit-appearance: none;
    margin: 20px 0;
    width: 100%;
  }
  input[type="range"]:focus {
    outline: none;
  }
  input[type="range"]::-webkit-slider-runnable-track {
    width: 100%;
    height: 4px;
    cursor: pointer;
    background: #03a9f4;
    border-radius: 25px;
  }
  input[type="range"]::-webkit-slider-thumb {
    height: 20px;
    width: 20px;
    border-radius: 50%;
    background: #fff;
    box-shadow: 0 0 4px 0 rgba(0, 0, 0, 1);
    cursor: pointer;
    -webkit-appearance: none;
    margin-top: -8px;
  }
  input[type="range"]:focus::-webkit-slider-runnable-track {
    background: #03a9f4;
  }
  .range-wrap {
    width: 500px;
    position: relative;
  }
  .range-value {
    position: absolute;
    top: -50%;
  }
  .range-value span {
    width: 30px;
    height: 24px;
    line-height: 24px;
    text-align: center;
    background: #03a9f4;
    color: #fff;
    font-size: 12px;
    display: block;
    position: absolute;
    left: 50%;
    transform: translate(-50%, 0);
    border-radius: 6px;
  }
  .range-value span:before {
    content: "";
    position: absolute;
    width: 0;
    height: 0;
    border-top: 10px solid #03a9f4;
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    top: 100%;
    left: 50%;
    margin-left: -5px;
    margin-top: -1px;
  }
</style>
