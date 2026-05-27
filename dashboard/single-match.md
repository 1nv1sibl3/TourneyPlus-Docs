# Single Match

Single Match is the fastest event flow in TourneyPlus.

## Main Pages

- `/matches`
- `/matches/[id]`
- `/matches/[id]/view`

## Clear Step-by-Step Flow

1. **Create the match**
   - Set match name and slot count.
   - Set registration and slot channels.

2. **Open registration**
   - Teams register through the bot.
   - Confirm slot list updates correctly.

3. **Close registration**
   - Lock entries before result stage.

4. **Open result intake**
   - If you use screenshots, open screenshot window.

5. **Fill result data**
   - **AI-enabled plan**: review parsed rank and kills.
   - **No AI plan**: enter rank and kills manually.

6. **Check scoring rows**
   - Rank
   - Position Point
   - Kill Point
   - Total Points

7. **Resolve warnings**
   - Red: rank conflict
   - Orange: uncertain/incorrect value

8. **Publish leaderboard**
   - Confirm warning prompt if any flagged rows remain.

## Scoring Rule

`Total Points = Position Point + Kill Point`

If a team has no valid rank and no valid kills, keep that team below teams with valid submitted values.

## Editing Rules

When opening result edit rows, values should reflect current saved values (not forced zero).
Manual edits should be intentional and clearly visible before publish.