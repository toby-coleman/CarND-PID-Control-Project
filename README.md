# PID control

This repo implements a PID controller to steer a vehicle around a track
simulation.

## PID parameters

Manual tuning was used to adjust each of the PID parameters:
* P: If too small, the car is unable to steer quickly enough to compensate
for any position error, however as it becomes larger the car tends to
oscillate around the road centre position.
* I: This term compensates for any steady-state error as the car approaches
the centre of the road.  This isn't particularly useful on this track, as the
turns in the road mean that steady-state error will not persist for long
anyway.
* D: The derivative term can help compensate for the oscillations
introduced as P gets larger.

This model was tuned manually:
* I set to zero;
* P increased until oscillations occur in the vehicle control (`P = 0.15`);
* D increased until the oscillations are sufficiently damped (`D = 8.0`).

The code:

    double throttle = 0.6 - 0.5 * fabs(steer_value);

sets smaller throttle values when the steering angle is largest to make
cornering easier.
