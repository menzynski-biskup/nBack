# nBackAlpha3
N-back Alpha 3

Try it here: https://pavlovia.org/vuandre1/nBackAlpha3

## URL parameters

The task accepts these query parameters (if provided, they are auto-filled and hidden from the start dialog):

- `participant` (example: `P001`)
- `session` (example: `001`)
- `group` (example: `A`)
- `time_of_day` (example: `morning`)

Example URL:

`https://pavlovia.org/vuandre1/nBackAlpha3/?participant=P001&session=001&group=A&time_of_day=morning`

## How the task works (brief)

- The participant sees instructions for 1-back, then 2-back, then 3-back.
- Each block starts after pressing `s`.
- In each trial, a white square appears in one grid location, then a fixation cross.
- Participant presses `space` only when the current location matches the required n-back position (1, 2, or 3 trials back).
- Stimulus locations and expected answers are preloaded from:
  - `nBackCond1.xlsx` (1-back)
  - `nBackCond2.xlsx` (2-back)
  - `nBackCond3.xlsx` (3-back)

## Results variables and coding

### Session-level variables

Saved in experiment metadata (from dialog and URL): `participant`, `session`, `group`, `time_of_day`, plus runtime fields such as `date`, `expName`, `psychopyVersion`, `OS`, `frameRate`.

### Trial condition variables (from `.xlsx` files)

- `square`: location code used to define position sequence.
- `loc1`, `loc2`: x/y coordinates used to place the square.
- `corrAns`: expected response coding:
  - `space` = target trial (participant should press `space`)
  - empty/`None` = non-target trial (participant should not respond)

### Trial response variables (in output `.csv`)

- `trialResp.keys`: key pressed (`space`) or empty if no response
- `trialResp.rt`: response time in seconds (recorded only when a key is pressed)
- `trialResp.corr`: correctness coding:
  - `1` = correct (correct keypress on target OR correct non-response on non-target)
  - `0` = incorrect (miss on target OR false alarm on non-target)

## Changelog:

- Changed trial routines to duplications
- An 's' press now starts the trial blocks
- Doubled the number of trials in each block
- The 's' presses before the trial blocks are no longer recorded in the '.csv' data results

# Todo:

- Remove extraneous columns in the '.csv' data results
