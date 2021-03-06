# IROS2015 - submitted: Human grasping using a handled Pisa/IIT SoftHand

This scenario has been designed to create the Grasp database necessary for the ``High-Level Planning for Dual Arm Object Passing Tasks'' work submitted to IROS2015,  using the following devices:
* [PhaseSpace](http://www.phasespace.com/)
* [SoftHand](http://www.qbrobotics.com/#!softhand/c1njg)
* Handle for SoftHand


#### Experiment protocol

The experiment is simple. Only a cylilnder is to be grasped as a test object for the paper. Several grasps were tried called bottom, bottom180, sideThumb, depending on the grasp used. 

Just type in one terminal `roslaunch iros2015_grasp_db uploadSetup.launch` and in another terminal `roscd iros2015_grasp_db/data`  and record as many defined grasps as you want by runnin `./startRecording.sh`.

The recording procedure was stopped manually so the bag file length is variable among the data. One experiment bag file contains several tries of the same grasp, so we can segment it later manually to select the best candidate poses for the high-level planner.

Notes on the recorded data:
 - Recall only raw sensor data is recorded in the bag files at their max frequency plus `/tf`. 
 - Recall that parameter for each grasp is saved to disk prior the recording to replicate the data processing. 

#### How to play the recorded data

1. Files containing the data for the IROS2015 submission can be downloaded [here](http://131.114.31.70:8080/share.cgi?ssid=0X5QnTM&fid=0X5QnTM&ep=LS0tLQ==). Uncompress it in the `data` folder.

2. Type `roslaunch iros2015_grasp_db playExperiment.launch experiment_name:=NAME`. This already loads the parameters used during the experiment.

If you want to have a specific information being published in a(several) topic(s), you can `ros topic YOUR_TOPIC` and hit `space` to pause the playback at the desired moment, and hit `s` to perform a tiny step on the playback. Check the terminal where you echoed the topic and take the required infromation, for instace, this procedure can be used to have a static grasp captured from the recording.
