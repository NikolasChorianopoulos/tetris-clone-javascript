# tetris-clone-javascript

# Grid

The grid and the Tetrominos are created using arrays for each shape and orientation. this is the grid numbering:

| [0]   | [1]   | [2]   | [3]   | [4]   | [5]   | [6]   | [7]   | [8]   | [9]   |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| [10]  | [11]  | [12]  | [13]  | [14]  | [15]  | [16]  | [17]  | [18]  | [19]  |
| [20]  | [21]  | [22]  | [23]  | [24]  | [25]  | [26]  | [27]  | [28]  | [29]  |
| [30]  | [31]  | [32]  | [33]  | [34]  | [35]  | [36]  | [37]  | [38]  | [39]  |
| [40]  | [41]  | [42]  | [43]  | [44]  | [45]  | [46]  | [47]  | [48]  | [49]  |
| [50]  | [51]  | [52]  | [53]  | [54]  | [55]  | [56]  | [57]  | [58]  | [59]  |
| [60]  | [61]  | [62]  | [63]  | [64]  | [65]  | [66]  | [67]  | [68]  | [69]  |
| [70]  | [71]  | [72]  | [73]  | [74]  | [75]  | [76]  | [77]  | [78]  | [79]  |
| [80]  | [81]  | [82]  | [83]  | [84]  | [85]  | [86]  | [87]  | [88]  | [89]  |
| [90]  | [91]  | [92]  | [93]  | [94]  | [95]  | [96]  | [97]  | [98]  | [99]  |
| [100] | [101] | [102] | [103] | [104] | [105] | [106] | [107] | [108] | [109] |
| [110] | [111] | [112] | [113] | [114] | [115] | [116] | [117] | [118] | [119] |
| [120] | [121] | [122] | [123] | [124] | [125] | [126] | [127] | [128] | [129] |
| [130] | [131] | [132] | [133] | [134] | [135] | [136] | [137] | [138] | [139] |
| [140] | [141] | [142] | [143] | [144] | [145] | [146] | [147] | [148] | [149] |
| [150] | [151] | [152] | [153] | [154] | [155] | [156] | [157] | [158] | [159] |
| [160] | [161] | [162] | [163] | [164] | [165] | [166] | [167] | [168] | [169] |
| [170] | [171] | [172] | [173] | [174] | [175] | [176] | [177] | [178] | [179] |
| [180] | [181] | [182] | [183] | [184] | [185] | [186] | [187] | [188] | [189] |
| [190] | [191] | [192] | [193] | [194] | [195] | [196] | [197] | [198] | [199] |

---

# L Tetromino Orientations

The L Tetromino is defined as:

```js
const lTetromino = [
  [1, width + 1, width * 2 + 1, 2],
  [width, width + 1, width + 2, width * 2 + 2],
  [1, width + 1, width * 2 + 1, width * 2],
  [width, width * 2, width * 2 + 1, width * 2 + 2],
];
```

With a grid `width = 10`, each orientation below is visualized **using grid indices** (starting at `[1]` for demonstration):

---

## Orientation 1: `[1, 11, 21, 2]`

```
|     |[1]  |[2]  |     |
|     |[11] |     |     |
|     |[21] |     |     |
```

- Vertical L shape: three blocks down from `[1]`, one block to the right at the top.

---

## Orientation 2: `[10, 11, 12, 22]`

```
|     |     |     |     |
|[10] |[11] |[12] |     |
|     |     |[22] |     |
```

- Horizontal L shape: three blocks across, one block down at the right end.

---

## Orientation 3: `[1, 11, 21, 20]`

```
|     |[1]  |     |     |
|     |[11] |     |     |
|[20] |[21] |     |     |
```

- Vertical L shape upside down: three blocks down from `[1]`, one block to the left at the bottom.

---

## Orientation 4: `[10, 20, 21, 22]`

```
|     |     |     |     |
|[10] |     |     |     |
|[20] |[21] |[22] |     |
```

- Horizontal L shape: three blocks across at the bottom, one block up at the left end.

---

### How the array works

Each array inside `lTetromino` contains the grid indices for the blocks of the L Tetromino in a given orientation, calculated based on the grid width.

For example, `[1, width + 1, width * 2 + 1, 2]` becomes `[1, 11, 21, 2]` for `width=10`.

This lets the code easily draw or rotate the Tetromino by switching which array of indices is used!
