# HAND CLIENT

## How to run

Ensure that you have set up the robot as instructed in [Robot bring-up](../docs/BRINGUP.md) and that r_hand_controller is up and running. If not, refer back to the [bring-up](../docs/BRINGUP.md).

Once the robot is running properly, open a new command window, and run the hand_gestures_node with the following command.
```
ros2 run hand_gestures hand_gestures_node
```
Then run the client for the right hand in a new command window with the command:

```
python3 client/hand_action_client.py 
```
For the left hand client run the following command in a new command window

```
python3 client/left_hand_action_client.py 
```
Both clients work in the same but for different hands

## How to use

Once the client is up and running you will be greeted by a command line interface asking for your next command.

```
Input command:
```

Type in the command you want and watch as the hand completes the action.

## The commands

Currently, the following actions are available.

| Action    | What it does                              |
| --------  | ----------------------------------------- | 
| open      | Extends all fingers                       | 
| fist      | Forms a fist                              | 
| scissors  | Extends index and middle finger           | 
| point     | Extends index finger                      | 
| thumbs_up | Gives a thumbs up!                        | 
| grasp     | Grasps an object                          | 
| hard_rock | Heavy metal                               | 
| pen_grasp | Grasps with index and middle finger       | 
| rps       | Plays a round of Rock-Paper_scissors      | 
| #trial     | #Allows you to put in your custom position | 

### Trial

As told above the trial command allows you to set a custom position for the fingers. This is done by asking a position for each finger separately. Each finger must be given a position as ROS2 does not allow the hand to move without specifying positions for all the joints in the r_hand_controller. 

## IMPORTANT THE CUSTOM STATES MUST BE BETWEEN -0.5 AND 2 YOU WILL BREAK THE HAND IF YOU GO BEYOND THESE

# HEAD GESTURE CLIENT

## How to run

Ensure that you have set up the robot as instructed in [Robot bring-up](../docs/BRINGUP.md). head_gestures_node also needs to be started up, which can be done with the following command:

```
ros2 run head_gestures head_gestures_node
```

Once the robot is running properly, open a new command window, and start the client with the following command.

```
python3 client/head_gesture_client.py 
```

## How to use

Once the client is up and running you will be greeted by a command line interface asking for your next command.

```
Input command:
```

Type in the command you want and watch as the head completes the action.

## The commands

Currently, the following actions are available.

| Gesture   | What it does                              |
| --------  | ----------------------------------------- | 
| nod       | Nods                                      | 
| shake     | Shakes head                               | 

Optionally, the following arguments are also available for the currently implemented gestures.

| Gesture   | What it does                                                               |
| --------  | -------------------------------------------------------------------------- | 
| magnitude | Sets the magnitude of the head movements in the gesture                    | 
| delay     | Sets the delay between the beginning of each head movement in the gesture  |
| duration  | Sets the duration of the individual head movements in the gesture          |

Arguments can be used by adding them after the command, separated by commas in the following format

```
command, argument1_name=argument1_value, argument2_name=argument2_value
```

Example commands:

```
nod
```
```
shake, magnitude=0.5, delay=0.5, duration=0.4
```
```
nod, duration=0.4
```

The client does not check argument validity, but invalid arguments are ignored by the face_gestures_node. The 'quit' and 'exit' commands do not take arguments.