# ROAR
ROAR simulator using Microsoft Excel VB Script

Route Optimization for Autonomous Robot (ROAR)

This project is about creating a model of 'left hand rule' maze solving algorithm to optimize the route between two locations connected through a static path. One of the use case scenarios of this application is on autonomous robot to move along the corridor from one room to another room on the same floor within a building.

How it works:

Step-1: Exploration/Learning

The robot will explore the entire floor by traveling the corridors and take note of the rooms locations. The robot will start in a certain position (room) and will move forward along the corridor until it reaches a junction. At every junctions, the robot will turn left whenever possible or otherwise it will go straight. The robot will only turn right when that is the only option available. Every time the robot makes a turn or goes straight at a junction, it will add that move into the path record. When it reached to the entrance of a room, it will take note of the room identity and add it into the path record. 
Subsequently, it will turn around, and continue the journey until it arrives back at the room where it started. By traveling this way, it guaranteed that robot will explore the entire floor and take note of all rooms in that floor. See picture for an example of path recording.


Step-2: Route Optimization

Once all the room locations has been found and recorded, the robot will be able to determine the route from a given room to another room based on the parth record. However, that route may not be the shortest as the learned path contains some redundant moves. To optimize the path, a 'left hand rule' optimization method is applied. This is achievable by replacing certain pre-determined move sequences with optimized moves. As a result, the route between those two rooms can be shorter than the original route found in the path record.
The moves sequences replacement is following the below rules:

L = Left turn, R = Right turn, S = Straight, T = Turn around

LTR replaced with T

STS replaced with T

RTL replaced with T

LTS replaced with R

RTS replaced with L

LTL replaced with S

RTR replaced with S

STL replaced with R

STR replaced with L

The optimization shall be conducted several times until the the route can not be optimized anymore. So, although during the learning process the robot only made left turn or going straight, the moves sequence replacement above includes replacing right turn moves which may occur as a result in the previous optimization process.

Step-3: Travel the path based on Optimized Route

When the optimized route is already achieved, the robot now can move based on that route. Every time the robot reached a junction, it shall make decision whether to turn left, turn right, or go straight according to the movement plan in the route.



