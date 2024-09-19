<script>
  let bord = Array(9).fill("");
  let name = "Tic Tac Toe";
  let currentPlayer = "X";
  let winner = null;

  function handelClick(squareNumber) {
    bord[squareNumber] === "";
    {
      // set square to the current player
      bord[squareNumber] = currentPlayer;

      if (checkWinner()) {
        winner = currentPlayer;
      } else {
        // switch player
        if (currentPlayer === "X") {
          currentPlayer = "O";
        } else {
          currentPlayer = "X";
        }
      }
    }
  }

  function checkWinner() {
    const lines = [
      [0, 1, 2],
      [3, 4, 5],
      [6, 7, 8], // rows
      [0, 3, 6],
      [1, 4, 7],
      [2, 5, 8], // columns
      [0, 4, 8],
      [2, 4, 6], // diagonals
    ];

    return lines.some(
      ([a, b, c]) => bord[a] && bord[a] === bord[b] && bord[a] === bord[c]
    );
  }
</script>

<main>
  <h1>Tic Tac Toe</h1>

  {#if winner}
    <p>Player {winner} wins!</p>
  {:else}
    <p>Current Player: {currentPlayer}</p>
  {/if}

  <div class="board">
    {#each bord as square, squareNumber}
      <button on:click={() => handelClick(squareNumber)}>{square}</button>
    {/each}
  </div>
</main>

<style>
  .board {
    display: grid;
    grid-template-columns: repeat(3, 100px);
  }

  button {
    width: 100px;
    height: 100px;
  }
</style>
