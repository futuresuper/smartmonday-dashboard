<script>
  export let age;
  export let updateAge;
  $: if (age) {
    updateAge(age);
  }
  let max = 75;
  let min = 16;
  let rStyle = "";

  const setNumberPosition = () => {
    const newValue = Number(((age - min) * 100) / (max - min + 0.4));
    const newPosition = 10 - newValue * 0.2;
    // console.log(newValue);
    // console.log(newPosition);
    rStyle = `calc(${newValue}% - 14px + (${newPosition}px))`;
  };
</script>

<div class="slidecontainer">
  <div class="range-wrap">
    <div class="range-value-container">
      <div class="range-value" id="rangeV" style={"left: " + rStyle}>
        {age}
      </div>
    </div>
    <input
      bind:value={age}
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
    height: 8px;
    cursor: pointer;
    background: $red;
    border-radius: 25px;
  }
  input[type="range"]::-webkit-slider-thumb {
    height: 26px;
    width: 26px;
    border-radius: 50%;
    background: #fff;
    box-shadow: 0 0 4px 0 rgba(0, 0, 0, 1);
    cursor: pointer;
    -webkit-appearance: none;
    margin-top: -9px;
  }
  .range-wrap {
    width: 100%;
    position: relative;
    padding: 40px;
  }
  .range-value-container {
    position: relative;
    width: 100%;
  }
  .range-value {
    position: absolute;
    top: -36px;
    font-size: 28px;
    font-weight: bold;
  }
</style>
