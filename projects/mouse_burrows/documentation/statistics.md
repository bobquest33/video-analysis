# Output statistics

## Time period statistics
These are statistics that can be calculated for any time period of the video.
Typically, we calculate the statistics for time slices of half an hour to see the
development over time. Additionally, these statistics can be calculated for
the entire video.
For each period, the following statistics can be calculated:

* `ground_removed`: The area of the region which was below the ground line in the
    first frame and is now above ground in the last frame.
* `ground_accrued`: The area of the region which was above the ground line in the
    first frame and is now below ground in the last frame.
* `time_spent_moving`: The total time the mouse spent moving around during the
    analysis period. The mouse is said to be moving if its speed is above a
    threshold value.
* `time_spent_digging`: The total time the mouse spent digging. Here, digging is
    defined by the mouse being close to the end of a burrow, independent of its
    other states. Consequently, this statistics reports the mouse as digging
    even if it is just sitting at the end of the burrow. 
* `mouse_speed_mean`: The mean speed of the mouse during the analysis period.
    Here, we assume a speed of zero for periods where we could not detect the
    mouse.
* `mouse_speed_mean_valid`: The mean speed of the mouse during the analysis period.
    The difference to the value above is that we here only included periods in
    which we could actually detect the mouse.
* `mouse_speed_max`: The maximal speed the mouse attained during the analysis
    period.
* `mouse_distance_covered`: The total distance the mouse covered over the
    analysis period.
* `mouse_trail_longest`: The longest distance the mouse has been under ground
    during the analysis period. This distance is given by the maximum over the
    length of all mouse trails. A mouse trail in turn is the path connecting
    the point of entrance with the current mouse position.
* `mouse_deepest_diagonal`: The maximum distance of the mouse to the ground
    line. The distance is the length of the shortest line connecting the mouse
    position to the ground line, irrespective of any burrows.
* `mouse_deepest_vertical`: The longest distance of the mouse vertically under
    the ground. This distance is given by the distance of the mouse to the point
    on the ground line that is directly above it, irrespective of any burrows.
    
Additionally, we save information about what time slice was actually analyzed:

* `frame_interval`: The index of the first and last frame taken into consideration
* `period_start`: The beginning of the analysis period in seconds 
* `period_end`: The end of the analysis period in seconds 
* `period_duration`: The duration of the analysis period in seconds 



## Full video statistics
These are additional statistics that are only produced for the entire video and 
not for individual time periods

* `burrow_area_total`: The total area of all burrow structures
* `burrow_length_total`: The total length of all burrow structures  
* `burrow_length_max`: The length of the longest burrow

All burrow statistics are currently obtained by sweeping the mouse trail over
time.
The mouse trail is given by the connecting line of the current mouse position
with the ground line.
The statistics are calculated until the end of the analysis period, which is
typically the end of the night.