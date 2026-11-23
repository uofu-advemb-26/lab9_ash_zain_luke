# Invariants from part 1

When any number of trains approach the crossing, the arm only raises
once every approach has an accompanying depart signal and
the alarm only stops when the arm has been up for 10 seconds.

Sensors, logic controller, and wiring for the 

Messages from the sensors are well-formed.

No physical obstruction of arms on the tracks.

## Find a counter-example sequence that makes an invariant false

(Property 0):
Starting in `idle`, `nb_approach` signal places the FSM in `ringing, arms up`,
then a `sb_approach` signal is sent,
but the state is not refreshed and the "elapsed" criteria is only
considering the northbound approach.

(Property 1):
Starting in `ringing, arms up`, a fast enough train that departs
prior to the `elapsed` signal triggering would lose a `nb_depart` signal.

## Invariants table

| number | arms_down | alarm_on | northbound_present | southbound_present | north_approach | south_approach | north_depart | south_depart | ringing | safety_hazard |
|--------|-----------|----------|--------------------|--------------------|----------------|----------------|--------------|--------------|---------|---------------|
| 0      | 0         | 0        | 0                  | 0                  | 6              | 5              | 0            | 0            | 0       |               |
| 1      | 0         | 0        | 0                  | 1                  | 7              | 5              | 1            | 4            | 5       | 0             |
| 2      | 0         | 0        | 1                  | 0                  | 14             | 14             | 4            | 6            | 6       | 0             |
| 3      | 0         | 0        | 1                  | 1                  | 15             | 15             | 13           | 14           | 15      | 0             |
| 4      | 0         | 1        | 0                  | 0                  | 6              | 5              | 4            | 4            | 0       |               |
| 5      | 0         | 1        | 0                  | 1                  | 7              | 5              | 5            | 4            | 13      |               |
| 6      | 0         | 1        | 1                  | 0                  | 6              | 7              | 4            | 6            | 14      |               |
| 7      | 0         | 1        | 1                  | 1                  | 7              | 7              | 5            | 6            | 15      |               |
| 8      | 1         | 0        | 0                  | 0                  | 0              | 0              | 0            | 0            | 0       |               |
| 9      | 1         | 0        | 0                  | 1                  | 0              | 0              | 0            | 1            | 0       |               |
| 10     | 1         | 0        | 1                  | 0                  | 0              | 0              | 1            | 0            | 0       |               |
| 11     | 1         | 0        | 1                  | 1                  | 0              | 0              | 1            | 1            | 0       |               |
| 12     | 1         | 1        | 0                  | 0                  | 0              | 0              | 0            | 0            | 1       | 0             |
| 13     | 1         | 1        | 0                  | 1                  | 0              | 1              | 0            | 0            | 1       | 0             |
| 14     | 1         | 1        | 1                  | 0                  | 1              | 0              | 0            | 0            | 1       | 0             |
| 15     | 1         | 1        | 1                  | 1                  | 1              | 1              | 0            | 0            | 1       | 0             |

