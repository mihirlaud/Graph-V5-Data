# Graph V5 Data
**Easy to use method of creating live graphs for the VEX V5 system.** \
This program reads data from the serial output from the V5 Brain allowing you to easily graph as many sets of data as you'd like in real-time.
## How to Use
Download the `graph.py` and `requirements.txt` files and run `pip install -r requirements.txt`. Then run `python graph.py` when you are ready to start graphing data. You can run this before or while the program on the V5 brain is running.

To graph the data, print out `graph_data` from your V5 program right before printing out the data you need.
```c
printf("graph_data\n");
```
Select which data to use by printing out a comma-separated list of the data labels followed by the data values, separated by `|`.\
The first value will be the x-axis that all following data points will use, which is often time.
```c
printf("time (ms),data1,data2|%d,%f,%f\n", time, data1, data2);
```
Here's an example that will graph the velocity of both flywheel motors as a function of time
```c
printf("time (ms),f1 velocity (rpm),f2 velocity (rpm)|%d,%.2f,%.2f\n", pros::millis(), fly1.get_velocity(), fly2.get_velocity);
```
You can print out as much other data as you'd like and the program will still function, as long as you follow the format and print the data after `graph_data`
### Controls
|Key|Command         |
|:-:|----------------|
|R  |Reset graph data|
|S  |Toggle scrolling|
## Notes
If you are having issues recognizing the V5 device, you can replace `port = find_port()` with `port = "COM1"` in main replacing `COM1` with the usb port your V5 brain is plugged into.
## Limitations
Currently, the program only supports having a single set of data for the x-axis shared by all the data sets.

There is currently no built-in way to export the data which is something I'd like to add. For now, you can right click the graph and use the context menu to export an image.

I hope to develop a full GUI in the future to make the program much more user-friendly.
