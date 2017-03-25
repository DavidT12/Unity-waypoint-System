# Unity-waypoint-System
Unity Path Follow System using waypoints

This is a C# file that will move your game object to the waypoints/coordinates you enter into it. You simple add in the waypoints/coordinates you would like your object to travel to and it will move in that direction. 
![alt tag](https://github.com/DavidT12/Unity-waypoint-System/blob/master/waypoints.gif?raw=true)

It works by comparing the current position of your object the “transform.position” to the first waypoint/coordinate. 

It then rotates the object to face the waypoint/coordinate using the “Quaternion.LookRotation” method. The speed of the rotation is controlled by “Quaternion.Slerp”.

The object is moved using “Rigidbody.AddForce”

To add waypoints, go to the method labelled “SetWaypoints” and add in the required coordinates. 
For example in the gif above I used 4 waypoints. To add them I used the following code:

        waypoints.Add(new Vector3(127f, 0.5f, 40f));
        waypoints.Add(new Vector3(127f, 0.5f, 90f));
        waypoints.Add(new Vector3(55f, 0.5f, 90f));
        waypoints.Add(new Vector3(40f, 0.5f, 47f));

Once you have added in the required waypoints/coordinates you still have 4 public variables to consider.

    public float force = 5;
    public Rigidbody rb;
    public float turn_speed = 1F;
    public float dis_changewaypoint = 10F;

force is used just to control the amount of force being applied to the object.

Rb is the Rigidbody of the object that needs to be added to the script. 

turn_speed is used to control the rate at which the object will turn.

dis_changewaypoint stands for distance from current waypoint to change to next waypoint. At some stage you need to change which waypoint you are looking for and you might not want to wait until you actually reach the first waypoint to start looking at the next one. How soon or late you want to make this change is up to you and can be set using this public variable. 
