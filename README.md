# Unofficial_Go2_Ros2_Sdk_Topic_INFO_
# topic (10HZ): /imu

```
ros2 topic info /imu
```

Type: go2_interfaces/msg/IMU
Publisher count: 1
Subscription count

```
ros2 interface show go2_interfaces/msg/IMU
```
float32[4] quaternion
float32[3] gyroscope
float32[3] accelerometer
float32[3] rpy
int8 temperature
```
ros2 topic echo imu
```
quaternion:
- 0.6851580142974854
- 0.004290999844670296
- -0.005257999990135431
- -0.7283629775047302
gyroscope:
- -0.011718000285327435
- 0.003195999888703227
- -0.005326000042259693
accelerometer:
- -0.015561999753117561
- 0.17358000576496124
- 9.531316757202148
rpy:
- 0.013539000414311886
- -0.0009539999882690609
- -1.6319140195846558
temperature: 79
---



# topic (2HZ): /point_cloud2

```
ros2 topic info /point_cloud2
```
Type: sensor_msgs/msg/PointCloud2
Publisher count: 1
Subscription count: 0
```
ros2 interface show sensor_msgs/msg/PointCloud2
```
This message holds a collection of N-dimensional points, which may contain additional information such as normals, intensity, etc. 
The point data is stored as a binary blob, its layout described by the contents of the "fields" array. 
The point cloud data may be organized 2d (image-like) or 1d (unordered). 
Point clouds organized as 2d images may be produced by camera depth sensors such as stereo or time-of-flight.
Time of sensor data acquisition, and the coordinate frame ID (for 3d points).

std_msgs/Header header
	builtin_interfaces/Time stamp
		int32 sec
		uint32 nanosec
	string frame_id

#2D structure of the point cloud. If the cloud is unordered, height is
#1 and width is the length of the point cloud.
uint32 height
uint32 width

#Describes the channels and their layout in the binary data blob.
PointField[] fields
	uint8 INT8    = 1
	uint8 UINT8   = 2
	uint8 INT16   = 3
	uint8 UINT16  = 4
	uint8 INT32   = 5
	uint8 UINT32  = 6
	uint8 FLOAT32 = 7
	uint8 FLOAT64 = 8
	string name      #
	uint32 offset    #
	uint8  datatype  #
	uint32 count     #

bool    is_bigendian # Is this data bigendian?
uint32  point_step   # Length of a point in bytes
uint32  row_step     # Length of a row in bytes
uint8[] data         # Actual point data, size is (row_step*height)

bool is_dense        # True if there are no invalid points
```
ros2 topic echo /point_cloud2
```
header:
  stamp:
    sec: 1745585914
    nanosec: 375928826
  frame_id: odom
height: 1
width: 82314
fields:
- name: x
  offset: 0
  datatype: 7
  count: 1
- name: y
  offset: 4
  datatype: 7
  count: 1
- name: z
  offset: 8
  datatype: 7
  count: 1
- name: intensity
  offset: 12
  datatype: 7
  count: 1
is_bigendian: false
point_step: 16
row_step: 1317024
data:
- 51
- 51
- 19
- 191
- 0
- 0
- 40
- 192
- 198
- 204
- 204
- 188
- 0
- 0
- 88
- 66
- 51
- 51
- 19
- 191
- 0
- 0
- 40
- 192
- 198
- 204
- 204
- 188
- 0
- 0
- 112
- 66
- 51
- 51
- 19
- 191
- 0
- 0
- 40
- 192
- 218
- 204
- 204
- 60
- 0
- 0
- 88
- 66
- 51
- 51
- 19
- 191
- 0
- 0
- 40
- 192
- 218
- 204
- 204
- 60
- 0
- 0
- 112
- 66
- 51
- 51
- 19
- 191
- 205
- 204
- 36
- 192
- 198
- 204
- 204
- 188
- 0
- 0
- 88
- 66
- 51
- 51
- 19
- 191
- 205
- 204
- 36
- 192
- 198
- 204
- 204
- 188
- 0
- 0
- 112
- 66
- 51
- 51
- 19
- 191
- 205
- 204
- 36
- 192
- 218
- 204
- 204
- 60
- 0
- 0
- 88
- 66
- 51
- 51
- 19
- 191
- 154
- 153
- 33
- 192
- 198
- 204
- 204
- 188
- 0
- 0
- 88
- 66
- '...'
is_dense: false
---

# topic (2HZ): /scan
```
ros2 topic info /scan
```
Type: sensor_msgs/msg/LaserScan
Publisher count: 1
Subscription count: 0

>>ros2 interface show sensor_msgs/msg/LaserScan
#Single scan from a planar laser range-finder
#If you have another ranging device with different behavior (e.g. a sonar
#array), please find or create a different message, since applications
#will make fairly laser-specific assumptions about this data

std_msgs/Header header # timestamp in the header is the acquisition time of
	builtin_interfaces/Time stamp
		int32 sec
		uint32 nanosec
	string frame_id
                             # the first ray in the scan.
                             #
                             # in frame frame_id, angles are measured around
                             # the positive Z axis (counterclockwise, if Z is up)
                             # with zero angle being forward along the x axis

float32 angle_min            # start angle of the scan [rad]
float32 angle_max            # end angle of the scan [rad]
float32 angle_increment      # angular distance between measurements [rad]

float32 time_increment       # time between measurements [seconds] - if your scanner
                             # is moving, this will be used in interpolating position
                             # of 3d points
float32 scan_time            # time between scans [seconds]

float32 range_min            # minimum range value [m]
float32 range_max            # maximum range value [m]

float32[] ranges             # range data [m]
                             # (Note: values < range_min or > range_max should be discarded)
float32[] intensities        # intensity data [device-specific units].  If your
                             # device does not provide intensities, please leave
                             # the array empty.
```
ros2 topic echo scan
```
header:
  stamp:
    sec: 1745584333
    nanosec: 839903053
  frame_id: base_link
angle_min: -3.1415927410125732
angle_max: 3.1415927410125732
angle_increment: 0.01745329238474369
time_increment: 0.0
scan_time: 0.03333333507180214
range_min: 0.0
range_max: .inf
ranges:
- 0.6032275557518005
- 0.379814475774765
- 0.6711400151252747
- 0.5594335198402405
- 0.44798675179481506
- 0.5168877840042114
- 0.5170098543167114
- 0.40610623359680176
- 0.6556911468505859
- 0.4756946563720703
- 0.5456791520118713
- 0.615639865398407
- 0.36614909768104553
- 0.43655985593795776
- 0.5075032711029053
- 0.719029426574707
- 1.0018634796142578
- 0.3999321162700653
- 0.40020716190338135
- 0.9293965697288513
- 0.6474065184593201
- 0.5065375566482544
- 0.4363345503807068
- 0.36622154712677
- 0.6149923205375671
- 0.5451332330703735
- 0.47544488310813904
- 0.654778242111206
- 0.4064086079597473
- 0.5164366364479065
- 0.6271740198135376
- 0.628026008605957
- 0.558896005153656
- 0.669575572013855
- 0.6020441651344299
- 0.6029821634292603
- 0.757868230342865
- 0.6465628147125244
- 0.6918306350708008
- 0.5806561708450317
- 0.737185537815094
- 0.6272820234298706
- 0.6728581786155701
- 0.8303431868553162
- 0.7199461460113525
- 0.6115950345993042
- 0.6571505069732666
- 0.7052876353263855
- 0.7064695358276367
- 0.7548648118972778
- 0.8509857058525085
- 0.6945523023605347
- 0.6951749324798584
- 0.7922766804695129
- 0.8441445231437683
- 0.9893127679824829
- 0.7363373041152954
- 0.8357588052749634
- 0.9844413995742798
- 1.18448805809021
- 0.7822914123535156
- 0.9328439831733704
- .inf
- 0.9809866547584534
- 0.881710410118103
- 1.2818175554275513
- 0.9837895631790161
- 0.9339144229888916
- 1.1367778778076172
- 0.9884213209152222
- 1.2412493228912354
- 1.0942566394805908
- 1.0448706150054932
- 1.1512904167175293
- 1.1029647588729858
- 1.2081987857818604
- 1.1101174354553223
- 1.2707535028457642
- 1.1719183921813965
- 1.1230946779251099
- 1.0751962661743164
- 1.138877511024475
- 1.0908842086791992
- 1.20645272731781
- 1.4281153678894043
- 1.380863904953003
- 1.4010741710662842
- 1.3562555313110352
- 1.4220194816589355
- 1.3778935670852661
- 1.6694624423980713
- 1.693013310432434
- 1.76179039478302
- 1.7184498310089111
- 1.7434654235839844
- 1.8123536109924316
- 1.7702710628509521
- 1.7980678081512451
- 1.686658263206482
- 1.6459397077560425
- 1.6757912635803223
- 1.8869584798812866
- 1.8479304313659668
- 1.879902720451355
- .inf
- .inf
- .inf
- .inf
- .inf
- .inf
- .inf
- .inf
- .inf
- 1.77470862865448
- 1.7432414293289185
- 1.7827085256576538
- 1.8226929903030396
- 1.7934626340866089
- 1.8345757722854614
- .inf
- 1.2674627304077148
- 1.3098422288894653
- 1.2412134408950806
- 1.2844594717025757
- 1.3281800746917725
- 1.2605493068695068
- 1.3050713539123535
- 1.3499765396118164
- '...'
intensities: []
---

# topic (10HZ): /go2_states
```
rostopic info /go2_states
```
Type: go2_interfaces/msg/Go2State
Publisher count: 1
Subscription count: 0
```
ros2 interface show go2_interfaces/msg/Go2State
```
uint8 mode
int32 progress
uint8 gait_type
float32 foot_raise_height
float32[3] position
float32 body_height
float32[3] velocity
float32[4] range_obstacle
int16[4] foot_force
float32[12] foot_position_body
float32[12] foot_speed_body
```
ros2 topic echo /go2_states
```
mode: 1
progress: 0
gait_type: 0
foot_raise_height: 0.0
position:
- 2.642322063446045
- -0.10871099680662155
- 0.30711400508880615
body_height: 0.3199999928474426
velocity:
- 0.00017100000695791095
- -0.0027099999133497477
- -0.019023999571800232
range_obstacle:
- 2.0
- 2.0
- 2.0
- 2.0
foot_force:
- 41
- 16
- 38
- 38
foot_position_body:
- 0.18079900741577148
- -0.1392419934272766
- -0.3073579967021942
- 0.18821200728416443
- 0.1423339992761612
- -0.3046570122241974
- -0.2012699991464615
- -0.15110599994659424
- -0.3074679970741272
- -0.2004459947347641
- 0.1487790048122406
- -0.31057101488113403
foot_speed_body:
- 0.00010099999781232327
- -0.011921999976038933
- 0.004786000121384859
- 0.02755099907517433
- 0.001180000021122396
- 0.0014070000033825636
- -0.010827000252902508
- 0.011924000456929207
- -0.0037799999117851257
- 0.0013830000534653664
- 0.01217699982225895
- -0.0024999999441206455
---



# topic (10HZ): /joint_states
```
ros2 topic info /joint_states
```
Type: sensor_msgs/msg/JointState
Publisher count: 1
Subscription count: 1
```
ros2 interface show sensor_msgs/msg/JointState
```
#This is a message that holds data to describe the state of a set of torque controlled joints.
#The state of each joint (revolute or prismatic) is defined by:
#the position of the joint (rad or m),
#the velocity of the joint (rad/s or m/s) and
#the effort that is applied in the joint (Nm or N).
Each joint is uniquely identified by its name
#The header specifies the time at which the joint states were recorded. All the joint states
#in one message have to be recorded at the same time.
#This message consists of a multiple arrays, one for each part of the joint state.
#The goal is to make each of the fields optional. When e.g. your joints have no
#effort associated with them, you can leave the effort array empty.
#All arrays in this message should have the same size, or be empty.
#This is the only way to uniquely associate the joint name with the correct
#states.

std_msgs/Header header
	builtin_interfaces/Time stamp
		int32 sec
		uint32 nanosec
	string frame_id

string[] name
float64[] position
float64[] velocity
float64[] effort
```
ros2 topic echo /go2_states
```
mode: 1
progress: 0
gait_type: 0
foot_raise_height: 0.0
position:
- 2.642322063446045
- -0.10871099680662155
- 0.30711400508880615
body_height: 0.3199999928474426
velocity:
- 0.00017100000695791095
- -0.0027099999133497477
- -0.019023999571800232
range_obstacle:
- 2.0
- 2.0
- 2.0
- 2.0
foot_force:
- 41
- 16
- 38
- 38
foot_position_body:
- 0.18079900741577148
- -0.1392419934272766
- -0.3073579967021942
- 0.18821200728416443
- 0.1423339992761612
- -0.3046570122241974
- -0.2012699991464615
- -0.15110599994659424
- -0.3074679970741272
- -0.2004459947347641
- 0.1487790048122406
- -0.31057101488113403
foot_speed_body:
- 0.00010099999781232327
- -0.011921999976038933
- 0.004786000121384859
- 0.02755099907517433
- 0.001180000021122396
- 0.0014070000033825636
- -0.010827000252902508
- 0.011924000456929207
- -0.0037799999117851257
- 0.0013830000534653664
- 0.01217699982225895
- -0.0024999999441206455
---



# topic (200-300HZ): /joy
```
rostopic info /joy
```
Type: sensor_msgs/msg/Joy
Publisher count: 1
Subscription count: 2
```
ros2 interface show sensor_msgs/msg/Joy
```
#Reports the state of a joystick's axes and buttons.
#The timestamp is the time at which data is received from the joystick.
std_msgs/Header header
	builtin_interfaces/Time stamp
		int32 sec
		uint32 nanosec
	string frame_id

#The axes measurements from a joystick.
float32[] axes

#The buttons measurements from a joystick.
int32[] buttons
```
ros2 topic echo /joy
```
---
header:
  stamp:
    sec: 1745586149
    nanosec: 939692449
  frame_id: joy
axes:
- -0.0
- 1.0
- 1.0
- -0.0
- -0.0
- 1.0
- 0.0
- 0.0
buttons:
- 0
- 0
- 0
- 0
- 0
- 0
- 0
- 0
- 0
- 0
- 0
---



# topic (200-300HZ): /cmd_vel
```
ros2 topic info /cmd_vel
```
Type: geometry_msgs/msg/Twist
Publisher count: 1
Subscription count: 1
```
ros2 interface show geometry_msgs/msg/Twist
```
#This expresses velocity in free space broken into its linear and angular parts.

Vector3  linear
	float64 x
	float64 y
	float64 z
Vector3  angular
	float64 x
	float64 y
	float64 z
```
ros2 topic echo /cmd_vel
```
## What you record
-
-
linear:
  x: -0.0
  y: -0.0
  z: 0.0
angular:
  x: 0.0
  y: 0.0
  z: 0.0
-



