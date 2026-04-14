# SOAR Agent for 2048

This repo is a small SOAR-based demo that plays the 2048 puzzle through a Java UI and a SOAR production file. It is a prototype for agent control flow and reward shaping, not a proven solver or production game bot.

## Problem

The goal is to connect a cognitive architecture to a simple, stateful game and let the agent reason over board state, possible moves, and a reward signal. The project explores how to represent a 4x4 2048 board as working memory and feed that state into SOAR decisions.

## Approach

- `Gui.java` provides the Swing interface, human controls, and the switch between human and agent play.
- `Demo.java` owns the board state, builds the working memory, loads `2048.soar`, and applies SOAR output commands back to the board.
- `2048.soar` contains the production rules that choose directions based on the board state and the reward input.
- The board is translated into per-tile working memory, including nearby values, wall markers, and a simple reward score derived from the board.

The UI supports manual play, single-step agent play, and a bulk run mode for repeated episodes. The bulk mode is useful for observing behavior over many games, but it is still a demo loop rather than a benchmark harness.

## Outcome

The end result is a playable 2048 prototype where you can:

- load the SOAR production file,
- switch between human and agent control,
- step the agent one move at a time, and
- run repeated games to inspect scores and highest tiles reached.

That makes this repo useful as an agent integration example, but not as a claim that SOAR has fully solved 2048.

## How To Run

The provided `makefile` expects a local SOAR installation and still contains hard-coded paths from the original development machine. Update the SOAR paths in `makefile` before building.

```bash
make
make run
```

In the UI, load `2048.soar`, then switch to agent play and use `Agent Step` or the repeated-run control.

## Limitations

- The build is tied to a local SOAR Java setup and is not portable out of the box.
- The agent uses a simple board reward and handcrafted working-memory encoding.
- `Run 1000` is a demo stress test, not a formal evaluation.
- Some commands in the GUI reference local debugger paths from the original environment and may need to be updated or skipped.









