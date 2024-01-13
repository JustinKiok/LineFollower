## Line Following Robot
The robot was built upon a simple concept: follow a line of painter’s tape on the floor. This concept was derived from many factors, but I wanted a simple project that could be accomplished with a robotics kit I already had. 
## Programming
This robotics kit only included one color sensor, which presented a fun and inventive challenge regarding turning. Multiple color sensors could detect where the tape would turn. To fix this problem, I planned on hardcoding the system to do 90-degree turns. However, this was difficult due to many variables that affected the result, including battery power, rivets on the floor, and the fact that I could not place the tape perfectly. 
I settled with a more consistent, accurate, and flexible solution. Whenever the color sensor see blue painter's tape, the robot would move forward. This was accomplished through a simple "if" function:
```
if (color.blue() > 175) {
    RM.setPower(0.1);
    LM.setPower(-0.1);
    FM.setPower(0.3);
}
```
If it didn't see blue, the robot would spin. When it found the tape, it would continue moving forward. This created a zig-zag movement when turning. 
```
if (color.blue() < 176) {
    RM.setPower(-0.2 * turndirection);
    LM.setPower(-0.2 * turndirection);
    FM.setPower(-0.2 * turndirection);
}
```
Black tape reversed the turning direction, telling the robot when it had to spin in another direction. This was done through modifying the "turndirection" variable. Since the color sensor only reads red, blue, and green, the robot would detect a lack of color in all three categories and multiply the "turndirection" variable by -1.
## Building
The robot design was pretty simple at first. I put together a chassis with motors and mounted the electronics onto the back. However, the weight of the motors and the electronics imbalanced the robot and caused it to tip over at the slightest encouragement. To fix this, I added two metal beams to hold the front motor up, which would lower the impact of the weight imbalance. While this would not increase gravity to any noticeable extent, it would increase the amount of work done to imbalance the robot, making it harder for it to tip over. This is because the energy to raise an object against gravity is increased by the distance over which the energy is applied. This successfully corrected the weight imbalance. 

[![Line Follower Video](https://img.youtube.com/shorts/DjIV31LQJm0.jpg)](https://www.youtube.com/shorts/DjIV31LQJm0)
