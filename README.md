# @sabaki/go-board [![Build Status](https://travis-ci.org/SabakiHQ/go-board.svg?branch=master)](https://travis-ci.org/SabakiHQ/go-board)

A Go board data type.

## Installation

Use npm to install:

~~~
$ npm install @sabaki/go-board
~~~

## Usage

~~~js
const Board = require('@sabaki/go-board')

let board = new Board([
    [ 0, 0, 0,-1,-1,-1, 1, 0, 1, 1,-1,-1, 0,-1, 0,-1,-1, 1, 0],
    [ 0, 0,-1, 0,-1, 1, 1, 1, 0, 1,-1, 0,-1,-1,-1,-1, 1, 1, 0],
    [ 0, 0,-1,-1,-1, 1, 1, 0, 0, 1, 1,-1,-1, 1,-1, 1, 0, 1, 0],
    [ 0, 0, 0, 0,-1,-1, 1, 0, 1,-1, 1, 1, 1, 1, 1, 0, 1, 0, 0],
    [ 0, 0, 0, 0,-1, 0,-1, 1, 0, 0, 1, 1, 0, 0, 0, 1, 1, 1, 0],
    [ 0, 0,-1, 0, 0,-1,-1, 1, 0,-1,-1, 1,-1,-1, 0, 1, 0, 0, 1],
    [ 0, 0, 0,-1,-1, 1, 1, 1, 1, 1, 1, 1, 1,-1,-1,-1, 1, 1, 1],
    [ 0, 0,-1, 1, 1, 0, 1,-1,-1, 1, 0, 1,-1, 0, 1,-1,-1,-1, 1],
    [ 0, 0,-1,-1, 1, 1, 1, 0,-1, 1,-1,-1, 0,-1,-1, 1, 1, 1, 1],
    [ 0, 0,-1, 1, 1,-1,-1,-1,-1, 1, 1, 1,-1,-1,-1,-1, 1,-1,-1],
    [-1,-1,-1,-1, 1, 1, 1,-1, 0,-1, 1,-1,-1, 0,-1, 1, 1,-1, 0],
    [-1, 1,-1, 0,-1,-1,-1,-1,-1,-1, 1,-1, 0,-1,-1, 1,-1, 0,-1],
    [ 1, 1, 1, 1,-1, 1, 1, 1,-1, 1, 0, 1,-1, 0,-1, 1,-1,-1, 0],
    [ 0, 1,-1, 1, 1,-1,-1, 1,-1, 1, 1, 1,-1, 1,-1, 1, 1,-1, 1],
    [ 0, 0,-1, 1, 0, 0, 1, 1,-1,-1, 0, 1,-1, 1,-1, 1,-1, 0,-1],
    [ 0, 0, 1, 0, 1, 0, 1, 1, 1,-1,-1, 1,-1,-1, 1,-1,-1,-1, 0],
    [ 0, 0, 0, 0, 1, 1, 0, 1,-1, 0,-1,-1, 1, 1, 1, 1,-1,-1,-1],
    [ 0, 0, 1, 1,-1, 1, 1,-1, 0,-1,-1, 1, 1, 1, 1, 0, 1,-1, 1],
    [ 0, 0, 0, 1,-1,-1,-1,-1,-1, 0,-1,-1, 1, 1, 0, 1, 1, 1, 0]
])

let move = board.makeMove(1, [9, 4])
~~~

## API

### Sign Map

The board arrangement is represented by an array of arrays. Each of those subarrays represent one row, all containing the same number of integers. `-1` denotes a white stone, `1` a black stone, and `0` represents an empty vertex.

#### Example

~~~js
[[ 0, 0, 1, 0,-1,-1, 1, 0, 0],
 [ 1, 0, 1,-1,-1, 1, 1, 1, 0],
 [ 0, 0, 1,-1, 0, 1,-1,-1, 0],
 [ 1, 1, 1,-1,-1,-1, 1,-1, 0],
 [ 1,-1, 1, 1,-1, 1, 1, 1, 0],
 [-1,-1,-1,-1,-1, 1, 0, 0, 0],
 [ 0,-1,-1, 0,-1, 1, 1, 1, 1],
 [ 0, 0, 0, 0, 0,-1,-1,-1, 1],
 [ 0, 0, 0, 0, 0, 0, 0,-1, 0]]
~~~

### Vertex

Board positions are represented by a vertex, i.e. an array of the form `[x, y]` where `x` and `y` are non-negative integers, zero-based coordinates. `[0, 0]` denotes the upper left position of the board.

---

### `class Board`

#### Constructors

##### `new Board([signMap])`

- `signMap` [`<SignMap>`](#sign-map) *(optional)* - Default: `[]`

##### `Board.fromDimensions(width, height)`

- `width` `<Integer>`
- `height` `<Integer>`

Returns a new `Board` instance with a [sign map](#sign-map) of the given dimensions that is filled with `0`.

#### Properties

##### `board.signMap`

[`<SignMap>`](#sign-map) - The underlying sign map of the board.

##### `board.width`

`<integer>` - The board width.

##### `board.height`

`<integer>` - The board height.

#### Board Arrangement Functions

##### `board.get(vertex)`
##### `board.set(vertex, sign)`
##### `board.has(vertex)`
##### `board.clear()`
##### `board.makeMove(sign, vertex[, options])`

#### Capture Count Functions

##### `board.getCaptures(sign)`
##### `board.setCaptures(sign, mutator)`

#### Board Property Functions

##### `board.isSquare()`
##### `board.isEmpty()`
##### `board.isValid()`

#### Topology Functions

##### `board.getDistance(vertex1, vertex2)`
##### `board.getNeighbors(vertex)`
##### `board.getConnectedComponent(vertex, predicate)`
##### `board.getChain(vertex)`
##### `board.getRelatedChains(vertex)`
##### `board.getLiberties(vertex)`
##### `board.hasLiberties(vertex)`

#### Helper Functions

##### `board.clone()`
##### `board.diff(board)`
##### `board.stringifyVertex(vertex)`
##### `board.parseVertex(coord)`
##### `board.getHandicapPlacement(count)`

