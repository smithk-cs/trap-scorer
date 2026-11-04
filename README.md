# Trap Line Scorer

A phone web page that scores a five-person trap squad live from a tripod behind the line.

- **Counts shots by sound.** Each gunshot moves the scoresheet to the next shooter in squad order (post 1 to post 5,
  five times, then everyone rotates one post right and post 5 walks to post 1). 125 shots make a 25-target round.
- **Calls hit or miss with the camera.** About a second after each shot it looks at what the orange clay did:
  broke into pieces, spread into fragments or vanished in mid-air (hit), or kept flying in one piece (miss).
  Partial and full breaks both count as hits.
- **Asks you when it isn't sure.** Unclear shots show **?** until you tap **Hit** or **Miss**. Tap any box on the
  scoresheet to change it.
- **Scoresheet** uses the usual marks (`/` hit, `O` miss), grouped by post, with totals per shooter and for the squad.
- **Copy scores** or **Download CSV** for a spreadsheet: a summary per shooter plus every shot with post, result and
  who made the call.

Everything runs on the phone. Video and audio are never uploaded or recorded, and scores stay on the phone (in the
browser's storage) until you copy or download them.

## Live page

`https://smithk-cs.github.io/trap-scorer/`

Hosted with GitHub Pages. To turn it on (once): **Settings → Pages → Build and deployment → Source: Deploy from a
branch → Branch: `main`, `/ (root)` → Save.** Every push to `main` updates the page within a minute or two.

The page must be opened from an `https://` address: phones only give the camera and microphone to secure pages.

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
| A shot was not counted | **+ Add shot**, then tap Hit or Miss |
| An extra shot was counted (neighboring field, dropped gear) | **Undo last shot** |
| Break between rounds, walking, talking near the phone | **Pause listening** |
| Camera called it wrong | Tap the box on the scoresheet, then **Hit** or **Miss** |
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
