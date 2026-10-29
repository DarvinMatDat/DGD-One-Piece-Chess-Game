# Chess project notes and classroom check record

## BG 01 — Rules and prototype

**Players and setup:** Two players. Board is 8 by 8. Each side begins with 16 pieces in the standard arrangement; White moves first.

**Turn:** On a turn, move one piece of your own color to a legal square. A move cannot capture a friendly piece or leave your own king in check. A piece may not pass through another piece except a knight. Captured pieces leave the board. The players alternate turns.

**Piece moves:** King one square any direction; queen any number along rank, file, or diagonal; rook along rank or file; bishop diagonally; knight in an L shape and may jump; pawn forward one square (or two from its starting square if both squares are clear), capturing one square diagonally forward. Pawns cannot move backward.

**Exceptions:** Castling moves the king two squares toward a rook, then the rook to the square beside the king. It is legal only if neither piece has moved, the squares between are clear, the king is not in check, and the king does not cross an attacked square. En passant captures an adjacent pawn that just advanced two squares, as though it moved one; it must happen on the immediately following turn. A pawn reaching the farthest rank is promoted immediately to queen, rook, bishop, or knight, chosen by the player.

**End:** Checkmate wins: the checked player has no legal move. Stalemate is a draw: the player is not checked but has no legal move. Draws are also recognized for threefold repetition, 50 moves by each player without pawn movement or capture, and insufficient mating material. Restart returns to the initial position, White to move, with empty history.

## BG 01 — Screen plan and six checks

Screen: 8×8 board with pieces, highlighted selection and legal destinations; current player and status message; move history; restart, undo, and short instructions. Colors use muted green and cream; piece symbols use Unicode.

Checks to run:
1. Open `index.html` and confirm the initial position and White to move.
2. White e2–e4 succeeds and turn changes to Black.
3. Illegal pawn move e2–e5 is rejected.
4. Select a Black piece on White's turn; it does not move.
5. Complete a checkmate or stalemate; game reports the correct result and ignores further moves.
6. Restart after moves; initial pieces, turn, message, and history reset.

**Checks performed in a JavaScript DOM simulation:** 64 squares display; e2–e4 is highlighted, executes, and changes the turn; e2–e5 is not offered; wrong-side input does not move a piece; Undo returns to White's initial turn; restart clears the move display and restores 64 squares; Fool's Mate ends with “Black wins by checkmate”; a click after checkmate leaves the result unchanged; restart after checkmate works. The app browser blocked opening a local `file:` URL, so the page has not been visually checked in a browser in this session.

## BG 02 — Complete gameplay checks

- Ordinary move changes board and turn; wrong-side selection and illegal destination are rejected.
- Special rules to demonstrate: castling, en passant, all four promotion choices, check, checkmate, stalemate.
- Undo reverses one move; restart resets the complete position.
- Fix found during checks: restarting initially did not clear the move-history panel. `start()` now clears it; restart was retested after a move and after checkmate.
- Post-game protection: `click()` ignores board clicks once the game ends; checked by clicking a square after Fool's Mate.
- Play two full games with classmates and record outcomes here before claiming those tests as completed: **Not yet observed in this session.**

## BG 03 — Lab release checks

Run these after downloading a fresh copy onto a second lab PC. Use the README directions without coaching the tester through each move.

| Check | What to do | Expected result | Observed |
|---|---|---|---|
| Fresh copy | Open `index.html` | Board displays without a server or network | Not yet observed |
| Classmate 1 | Give only README directions; observe play | Tester can start and complete moves | Not yet observed |
| Classmate 2 | Repeat with another player | Tester can start and complete moves | Not yet observed |
| Unusual input | Click after game ends | Position and result remain unchanged | Not yet observed |
| Retest fix 1 | Record a real tester issue and chosen fix | Issue no longer occurs | Not yet observed |
| Retest fix 2 | Record a second real tester issue and chosen fix | Issue no longer occurs | Not yet observed |

Do not fill in observations until performed. This file documents the release procedure; it does not claim classmates or another PC were available during creation.

## Explain the code

`chess.js` stores the 64 board squares in `board`, the active side in `turn`, castling/en-passant rights in `rights` and `ep`, and draw counters in `half` and `positions`. `legal()` generates possible moves and filters out any move leaving that side's king attacked. `click()` handles board input and rejects wrong-side or unhighlighted destinations. `doMove()` applies the move, updates rights/counters/turn, checks for an ending, and redraws the screen. `start()` restores the complete starting state.

**AI suggestion tried:** Use a 64-item array, generate candidate moves, then filter moves that expose the king. This keeps the board state compact and lets the same legal-move check protect both normal moves and checkmate detection. The implementation is in `chess.js` (`board`, `pseudo()`, `legal()`, and `doMove()`).
