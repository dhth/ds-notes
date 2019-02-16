# Robot Localization

We're concerned with two things:
- measurement
- motion

## Measurement
Means updating our belief (and renormalizing our distribution).

We gain information when we measure,ie, entropy decreases.

## Motion
Means keeping track of where all of our probability "went" when we moved (which means using the law of Total Probability).

We lose information when we (or the robot) move(s), ie, entropy increases.