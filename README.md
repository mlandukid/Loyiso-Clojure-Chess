[![Build Status](https://travis-ci.org/replomancer/Swordfight.svg?branch=master)](https://travis-ci.org/replomancer/Swordfight)

# Swordfight


"*A game of chess is like a sword fight. You must think first before you move.*"
([Shaolin and Wu Tang](https://en.wikipedia.org/wiki/Shaolin_and_Wu_Tang))

Swordfight is a chess engine (no GUI, just a chess AI). It's CECP-compatible and
works with XBoard GUI.


## Usage

1. Download [the latest release jar file](https://github.com/replomancer/Swordfight/releases).
2. Install [XBoard](https://www.gnu.org/software/xboard/) (should be available
   in your favorite package manager).
3. Run `xboard` and choose `Engine -> Load New 1st Engine`.
   To add Swordfight as a new engine you need to set "Engine Directory" to
   to the directory containing the jar file and type `java -jar <jar_filename>`
   in "Engine Command". This will make Swordfight play as black.
4. Play.

Alternatively if you want to run the latest version from the repository:
1. Download this repo.
2. Install [Leiningen](http://leiningen.org/) (requires Java JDK version 6 or
   later).
3. Install [XBoard](https://www.gnu.org/software/xboard/).
4. Run `xboard` and choose `Engine -> Load New 1st Engine`.
   To add Swordfight as a new engine you need to point to the repo directory
   and set `lein run` as command. This will make Swordfight play as black.
5. Play.

Swordfight currently uses parallelized alpha-beta pruning (YBWC) with Tomasz Michniewski's [simplified evaluation function](http://chessprogramming.wikispaces.com/Simplified+evaluation+function). If you run `xboard -debug` there will be some debugging info in the `xboard.debug` file.

![XBoard window](https://raw.githubusercontent.com/replomancer/Swordfight/master/doc/mexican_defense.png)


You can also play without a GUI by running `lein run` and using a command line interface
like in the session below (user input is after the `>` prompt). A monospaced font in your
terminal is highly recommended for the debug output (chess board):

```
# {:xboard-mode false, :debug-mode true, :edition-current-color W}
# {:white-can-castle-ks true, :black-can-castle-qs true, :last-move [     ], :edited false, :turn W, :black-can-castle-ks true, :moves-cnt 0, :white-can-castle-qs true}
#
# 8  ♜ ♞ ♝ ♛ ♚ ♝ ♞ ♜
# 7  ♟ ♟ ♟ ♟ ♟ ♟ ♟ ♟
# 6                 
# 5                 
# 4                 
# 3                 
# 2  ♙ ♙ ♙ ♙ ♙ ♙ ♙ ♙
# 1  ♖ ♘ ♗ ♕ ♔ ♗ ♘ ♖
#
#    a b c d e f g h
#
> e2e4
# {:white-can-castle-ks true, :black-can-castle-qs true, :last-move [e2 e4], :edited false, :turn B, :black-can-castle-ks true, :moves-cnt 1, :white-can-castle-qs true}
#
# 8  ♜ ♞ ♝ ♛ ♚ ♝ ♞ ♜
# 7  ♟ ♟ ♟ ♟ ♟ ♟ ♟ ♟
# 6                 
# 5                 
# 4          ♙      
# 3                 
# 2  ♙ ♙ ♙ ♙   ♙ ♙ ♙
# 1  ♖ ♘ ♗ ♕ ♔ ♗ ♘ ♖
#
#    a b c d e f g h
#
move b8c6
# {:xboard-mode false, :debug-mode true, :edition-current-color W}
# {:white-can-castle-ks true, :black-can-castle-qs true, :last-move [b8 c6], :edited false, :turn W, :black-can-castle-ks true, :moves-cnt 2, :white-can-castle-qs true}
#
# 8  ♜   ♝ ♛ ♚ ♝ ♞ ♜
# 7  ♟ ♟ ♟ ♟ ♟ ♟ ♟ ♟
# 6      ♞          
# 5                 
# 4          ♙      
# 3                 
# 2  ♙ ♙ ♙ ♙   ♙ ♙ ♙
# 1  ♖ ♘ ♗ ♕ ♔ ♗ ♘ ♖
#
#    a b c d e f g h
#
>
```

I think the unicode chess pieces look pretty neat!

♜ ♖ ♞ ♘ ♝ ♗ ♛ ♕ ♚ ♔ ♟ ♙

Depending on the terminal the colors may be confusing. ♜ is black.

## License

Distributed under the 2-clause BSD license.
