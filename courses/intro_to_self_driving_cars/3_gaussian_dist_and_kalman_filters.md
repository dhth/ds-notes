# Gaussian Distribution

![](https://i.imgur.com/Eroeb2F.png)

Variance relates to confusion and certainity. 

Wider gaussian curve -> higher variance -> higher confusion --> lower certainity

Narrower gaussian curve -> lower varia

Kalman filters is that they combine somewhat inaccurate sensor measurements with somewhat inaccurate predictions of motion to get a filtered location estimate that is better than any estimates that come from only sensor readings or only knowledge about movement.nce -> lower confusion --> higher certainity

# Kalman Filters

2 stages:
- measurement update (using Bayes' rule)
- motion update (using total probability distribution)

## Measurement update
![](https://i.imgur.com/5UMhlpS.png)

Posterior peak is higher as measurement increases certainity.

## Motion update
![](https://i.imgur.com/qRo4qlw.png)

Prediction peak is lower as there's uncertainity involved with motion.

Kalman filters combine somewhat inaccurate sensor measurements with somewhat inaccurate predictions of motion to get a filtered location estimate that is better than any estimates that come from only sensor readings or only knowledge about movement.