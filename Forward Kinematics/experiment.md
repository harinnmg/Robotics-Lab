Go to the link and copy
https://colab.research.google.com/drive/1UQ45sbfZoLPp3M34B1Wntk5NO0i-uUAL#scrollTo=IeqBREFcStjE

# Inverse Kinematics
Go to following website and download the following
https://github.com/xArm-Developer/xarm_ros
or
https://drive.google.com/drive/folders/1uSsd03_O8pYyoV8pMSt20cNS7_DvspYZ?usp=sharing

# Code
```
#!/usr/bin/env python3
import rospy
import tf

if __name__ == '__main__':
    rospy.init_node('tf_listener')
    listener = tf.TransformListener()

    rate = rospy.Rate(10.0)
    while not rospy.is_shutdown():
        try:
            (trans, rot) = listener.lookupTransform('/link1', '/link2', rospy.Time(0))
            # trans contains the translation vector (x, y, z)
            # rot contains the rotation quaternion (x, y, z, w)
            rospy.loginfo("Transform from frame1 to frame2: translation={}, rotation={}".format(trans, rot))
        except (tf.LookupException, tf.ConnectivityException, tf.ExtrapolationException):
            continue

        rate.sleep()
```
