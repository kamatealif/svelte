<script>
  let display = "0";

  const appendToDisplay = (value) => {
    if (display === "0" && value !== ".") {
      display = value;
    } else {
      display += value;
    }
  };

  const clearDisplay = () => {
    display = "0";
  };

  const deleteLast = () => {
    display = display.length > 1 ? display.slice(0, -1) : "0";
  };

  const calculateResult = () => {
    try {
      display = eval(display).toString(); // Caution: Avoid `eval` in production!
    } catch (error) {
      display = "Error";
    }
  };
</script>

<style>
  html,
  body,
  .app {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
    background: #1e1e1e;
    display: flex;
    justify-content: center;
    align-items: center;
    font-family: Arial, sans-serif;
    color: #fff;
  }

  .calculator {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 90%;
    max-width: 400px;
    height: auto;
    padding: 20px;
    background: #1e1e1e;
    border-radius: 12px;
    box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
  }

  .display {
    width: 100%;
    padding: 20px;
    margin-bottom: 20px;
    font-size: 2rem;
    background: #333;
    color: magenta;
    border: none;
    border-radius: 8px;
    text-align: right;
    box-shadow: inset 0 4px 10px rgba(0, 0, 0, 0.3);
  }

  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
    width: 100%;
  }

  .button {
    padding: 15px;
    font-size: 1.2rem;
    font-weight: bold;
    color: #fff;
    background: magenta;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: transform 0.2s, background-color 0.2s;
  }

  .button:active {
    transform: scale(0.95);
  }

  .button.operation {
    background: #ff007f;
  }

  .button.clear {
    background: #d9534f;
  }

  .button:hover {
    background: #d4007a;
  }

  .button.zero {
    grid-column: span 2;
  }
</style>

<div class="app">
  <div class="calculator">
    <input class="display" type="text" value={display} disabled />
    <div class="buttons">
      <button class="button clear" on:click={clearDisplay}>C</button>
      <button class="button" on:click={deleteLast}>DEL</button>
      <button class="button operation" on:click={() => appendToDisplay("/")}>/</button>
      <button class="button operation" on:click={() => appendToDisplay("*")}>*</button>

      <button class="button" on:click={() => appendToDisplay("7")}>7</button>
      <button class="button" on:click={() => appendToDisplay("8")}>8</button>
      <button class="button" on:click={() => appendToDisplay("9")}>9</button>
      <button class="button operation" on:click={() => appendToDisplay("-")}>-</button>

      <button class="button" on:click={() => appendToDisplay("4")}>4</button>
      <button class="button" on:click={() => appendToDisplay("5")}>5</button>
      <button class="button" on:click={() => appendToDisplay("6")}>6</button>
      <button class="button operation" on:click={() => appendToDisplay("+")}>+</button>

      <button class="button" on:click={() => appendToDisplay("1")}>1</button>
      <button class="button" on:click={() => appendToDisplay("2")}>2</button>
      <button class="button" on:click={() => appendToDisplay("3")}>3</button>
      <button class="button operation" on:click={calculateResult}>=</button>

      <button class="button zero" on:click={() => appendToDisplay("0")}>0</button>
      <button class="button" on:click={() => appendToDisplay(".")}>.</button>
    </div>
  </div>
</div>
