# Trap Line Scorer

A phone web page that scores a five-person trap squad live from a tripod behind the line.

- **Counts shots by sound.** Each gunshot moves the scoresheet to the next shooter in squad order (post 1 to post 5,
  five times, then everyone rotates one post right and post 5 walks to post 1). 125 shots make a 25-target round.
- **Calls hit or miss with the camera.** About a second after each shot it looks at what the orange clay did:
  broke into pieces, spread into fragments or vanished in mid-air (hit), or kept flying in one piece (miss).
  Partial and full breaks both count as hits. It also tracks the clay's flight path: a sudden turn or slow-down right
  after the shot supports a hit. A clay that only changes course, with no broken piece seen, is marked **?** for you
  to check, because a target needs a visible piece broken to score.
- **Photographs every shot.** A burst of nine pictures from the moment of the shot to about 0.75 s after. Tap any
  score on the scoresheet to open them: the viewer zooms in on where the clay was (dashed circle), **Play** runs the
  burst like a slow-motion clip, and you can confirm or change the call right there.
- **Asks you when it isn't sure.** Unclear shots show **?** until you tap **Hit** or **Miss**. You can also mark any
  shot unknown yourself with the **?** button. Unknown shots don't count toward the total until you decide.
- **Misses by direction.** The camera notes which way each target was flying (left, center/straightaway or right
  of the trap house, seen from behind the line). A table under the scoresheet shows, for each shooter and the squad,
  what share of their misses went each way and how many targets thrown that way they missed (for example "60% left,
  3 of 4 missed"). Fix any direction in the shot's photos. The **Center band** setting (default ±15°) sets how wide
  "straightaway" is.
- **Scoresheet** uses the usual marks (`/` hit, `O` miss), grouped by post, with totals per shooter and for the squad.
- **Copy scores** or **Download CSV** for a spreadsheet: a summary per shooter (including misses by direction) plus
  every shot with post, result, target direction and who made each call.

Everything runs on the phone. Video and audio are never uploaded or recorded. The shot photos and the scores are
saved only on that phone (in the browser's storage) and are deleted when you start a new round.

## Live page

`https://smithk-cs.github.io/trap-scorer/`

Hosted with GitHub Pages. To turn it on (once): **Settings → Pages → Build and deployment → Source: Deploy from a
branch → Branch: `main`, `/ (root)` → Save.** Every push to `main` updates the page within a minute or two.

The page must be opened from an `https://` address: phones only give the camera and microphone to secure pages.

## Team app

The scorer works with the [trap team app](https://github.com/smithk-cs/trap-team). On an event's page there, each squad
has a **Score squad N on the phone** button. It opens this page with that squad's names in post order (squads with
empty posts work too: fewer shooters, 25 targets each). When the round is done, tap **Send scores to team app**: each
shooter's round, with misses by direction, is saved to the event. Shots still marked **?** are left out (you're asked
first). Sending twice never counts a round twice; tap **Start next round** for the squad's next 25. **Stop using this
squad** goes back to the five names in settings.

## Test mode

Tap **Test mode** at the top. It uses a separate practice scoresheet that is never saved or mixed into your real round;
**Exit test mode** brings your real round back exactly as it was.

- **Run simulated range:** the phone generates a video of a trap field with a clay about every 3 seconds (clean breaks,
  dusted targets, small chips and misses) and runs it through the same shot counting, camera calls and photos as a
  real round. The app knows what really happened to each simulated clay, so the test bar shows how many camera calls
  were right, wrong or left for you. Tap any score to see its photos and the real result. No gun, range or camera needed.
- **Start camera & mic:** practice with your own camera and microphone. Clap to make a shot, and use it to check camera
  aim, the sky line and microphone sensitivity before a real round.

## At the range

1. Put the phone on a tripod 10–15 feet behind the line, in landscape, aimed so the sky above and beyond the trap
   house fills most of the picture. Plug it in or start with a full battery; the screen stays on.
2. Open the page in Safari (iPhone) or Chrome (Android) and add it to the home screen.
3. Open **Squad & settings** and enter names in the order they start (post 1 to post 5).
4. Tap **Start camera & mic** and allow both.
5. **Sky line:** drag the slider so the dashed yellow line sits just below where clays fly. Orange things below it
   (vests, trap house paint, cones) are ignored. Anything orange that sits still for a second or more is ignored too.
6. **Check the clays:** throw a few targets. Cyan boxes on the video show what the camera thinks is a clay. If clays
   don't get boxes, use the phone's 2× zoom or move the tripod closer to the line.
7. **Check the microphone:** fire a shot and watch the level bar. Gunshots should cross the white mark; talking should
   not. Adjust **Microphone sensitivity** if needed.

During the round:

| Situation | What to do |
|---|---|
| Not sure whether it was a hit | Tap the score to see the photos, or tap **?** to decide later |
| Done shooting, or moving the phone | **Stop camera & mic** (the scoresheet and photos are kept; **Start** continues the round) |
| A shot was not counted | **+ Add shot**, then tap Hit or Miss |
| An extra shot was counted (neighboring field, dropped gear) | **Undo last shot** |
| Break between rounds, walking, talking near the phone | **Pause listening** |
| Camera called it wrong | Tap the box on the scoresheet, check the photos, then **Hit** or **Miss** |
| No-bird / re-throw | Nothing: no shot is fired, so nothing is counted |

**First few practices:** turn off *Accept camera calls automatically*. The camera then only suggests a call and you
confirm each one, so you can see how often it agrees with you before trusting it.

## Limits of this prototype

- Tested with simulated video and gunshot audio, not yet with real range footage.
- At 30+ yards a clay is only a few pixels wide on a phone camera, so small chips are often left as **?**.
- Looks for **orange** clays against **sky**. Other colors, tree lines or an orange sunset sky work poorly.
- Assumes a full squad of five.
- Phone browsers give live video at 30–60 fps; slow-motion modes are not available to a web page.

## Files

- `index.html`: the whole app (HTML, CSS and JavaScript in one file, no build step, no server).
