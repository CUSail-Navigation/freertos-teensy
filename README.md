## CUSail Teensy FreeRTOS Code

This codebase contains the files necessary for the boat to run purely off of a Teensy 4.0. This move is necessary for the long-term goals of CUSail - in particular, it's necessary to allow for the boat to achieve a level of power efficiency which could be maintained by a solar panel. Much of this code is ported over from the ROS2 nodes found on the competition Navigation stack.

FreeRTOS is utilized (instead of a basic control loop) for better control over process timings and more precise control over shared resources. A later goal of this project is to have 2 Teensys on the boat, with one able to take control in the event that the other fails; FreeRTOS will help to ensure that both Teensys have the same sets of data at all times, and make the process of switching from 2 to 1 Teensys seamless from a software perspective.

# Features

Once completed, the Teensy will be able to interface with an Xbee module to take radio inputs. With that, the boat could either be controlled purely with RC, or a destination point could be inputted and the boat could navigate autonomously. The Teensy will optionally be able to interface with a more powerful boat computer - that computer could perform higher-level tasks (like event-specific algorithms, CV/ML tasks, webserver hosting).

# Limitations

Teensy-only use of the boat is not designed with competition events in mind. This reflects the Nav algo stack, which abstracts waypoints and competition actions into 2 separate entities (event algos decide end-points, while the main sail algo decides how the boat should get to that end-point). If the main PC is on the boat, this project could be thought of as shifting the main algo from the main PC onto the Teensy, while keeping the event algos on the main PC.

Computationally-intensive tasks (such as CV/ML), or tasks which require a more feature-packed OS (webserver hosting with Ngrok) cannot be performed on the Teensy.
