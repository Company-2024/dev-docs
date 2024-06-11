# How to Use Black Code Formatter

## Tips
* To ignore formatting for certain lines of code, wrap the code with comments `#fmt: off` and `#fmt: on`  e.g.
    ```
    # fmt: off
    np.array(
        [
            [1, 0, 0, 0],
            [0, -1, 0, 0],
            [0, 0, 1, 0],
            [0, 0, 0, -1],
        ]
    )
    # fmt: on
    ```