
J'ai oppéré des changements dans fw_path_navigation_params qui sont en fait des contantes qui permettent de définir quels sont les constante appliquée sur la navigation du drone

```cpp
/**
 * The aircraft's wing span (length from tip to tip).
 *
 * This is used for limiting the roll setpoint near the ground. (if multiple wings, take the longest span)
 *
 * @unit m
 * @min 0.1
 * @decimal 1
 * @increment 0.1
 * @group FW Geometry
 */
PARAM_DEFINE_FLOAT(FW_WING_SPAN, 0.1f);

/**
 * Height (AGL) of the wings when the aircraft is on the ground.
 *
 * This is used to constrain a minimum altitude below which we keep wings level to avoid wing tip strike. It's safer
 * to give a slight margin here (> 0m)
 *
 * @unit m
 * @min 0.0
 * @decimal 1
 * @increment 1
 * @group FW Geometry
 */
PARAM_DEFINE_FLOAT(FW_WING_HEIGHT, 0.0);
/**
 * Minimum groundspeed
 *
 * The controller will increase the commanded airspeed to maintain
 * this minimum groundspeed to the next waypoint.
 *
 * @unit m/s
 * @min 0.0
 * @max 40
 * @decimal 1
 * @increment 0.5
 * @group FW TECS
 */
PARAM_DEFINE_FLOAT(FW_GND_SPD_MIN, 40.0f);

/**
 * Bit mask to set the automatic landing abort conditions.
 *
 * Terrain estimation:
 * bit 0: Abort if terrain is not found
 * bit 1: Abort if terrain times out (after a first successful measurement)
 *
 * The last estimate is always used as ground, whether the last valid measurement or the land waypoint, depending on the
 * selected abort criteria, until an abort condition is entered. If FW_LND_USETER == 0, these bits are ignored.
 *
 * TODO: Extend automatic abort conditions
 * e.g. glide slope tracking error (horizontal and vertical)
 *
 * @min 0
 * @max 3
 * @bit 0 Abort if terrain is not found (only applies to mission landings)
 * @bit 1 Abort if terrain times out (after a first successful measurement)
 * @group FW Auto Landing
 */
PARAM_DEFINE_INT32(FW_LND_ABORT, 0);
```
