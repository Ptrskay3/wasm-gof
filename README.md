## Conway's game of life

This is an implementation of Conway's game of life in Rust and Javascript, based on [this material.](https://rustwasm.github.io/docs/book/) The grid size is 32 x 32, but implements periodic universe, where cells on the edges have neighbors at the opposite side of the grid.

### Introduction

The Conway's game of life is zero-player game, which means that everything is determined from the inital state of the game. The game space is a 2D orthogonal infinite grid of cells, each of which is in one of two possible states: dead or alive. Every cell interacts with its eight neighbours (so cells are diagonally adjacent too). At a given timestamp there is four rules which evolves the system:

  1. Any live cell with fewer than two live neighbours dies, as if by underpopulation.
  2. Any live cell with two or three live neighbours lives on to the next generation.
  3. Any live cell with more than three live neighbours dies, as if by overpopulation.
  4. Any dead cell with exactly three live neighbours becomes a live cell, as if by reproduction.

Read more [at Wikipedia.](https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life)

### Building the project

First, we need to compile the Rust code to WASM. To do that, you need to install the nightly version of Rust, and add wasm as a target.

```shell
# Install nightly
rustup toolchain install nightly

# Add wasm as target
rustup target add wasm32-unknown-unknown --toolchain nightly
```

After cloning, run
```shell
wasm-pack build
```
in the root directory, where `Cargo.toml` is.

Note that on Windows you might need to install wasm-pack manually. It's on [this link](https://rustwasm.github.io/wasm-pack/installer/).

After that, change to the `front` directory, and run
```shell
npm start
```
which will start the development server on `localhost:8080`. Every time you make a change in the Rust code, you need to recompile it to have effect.

### Improvements

* Add game speed controls
* Add interesting patterns
* Styling