# Chess

A local, two-player chess game for a classroom lab PC. No install, account, server, or external art/audio is required.

## Open and play

Open `index.html` in a current desktop or mobile browser. White moves first. Click a piece, then a highlighted square. Click **Undo move** to take back one move; **Restart game** resets the board and move history.

The pieces are illustrated SVG portraits: Luffy is king, Zoro queen, Brook knight, and Chopper pawn. Nami marks bishops on light squares and Usopp bishops on dark squares. Jinbei marks rooks on light squares and Franky rooks on dark squares. The character portraits are simple original code-drawn icons, not copied show artwork.

## Rules included

Standard chess setup and alternating turns. Pieces move by standard chess movement; pieces cannot move through blockers (except the knight), capture friendly pieces, or leave their king in check. Includes check, checkmate, stalemate, castling, en passant, and promotion to queen, rook, bishop, or knight. Classroom-friendly automatic draws are recognized by threefold repetition, the 50-move rule, stalemate, and insufficient mating material. There is no chess clock or online play.

## Files

- `index.html` — board, directions, controls, and page styling.
- `chess.js` — board state, legal move generation, rule checks, turn changes, ending conditions, and the character portraits.

## Known limitations

This is a classroom recreation, not a tournament-certified chess implementation. There is no clock, resignation, claim-based draw UI, or automatic fivefold/75-move draw handling. Threefold repetition and the 50-move draw are declared automatically for simpler classroom play. The game has not been observed on a second lab PC or played by two classmates in this session; use the release checklist in `PROJECT_NOTES.md` to record those real-world checks.

## Credits

Game code, interface, and original SVG portrait icons created with AI assistance (OpenAI Codex). No external images, sounds, libraries, or network requests are used.
