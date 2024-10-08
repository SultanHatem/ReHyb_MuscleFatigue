These are sEMG recordings from three muscle fatiguing experiments.

Data was recorded using a PLUX Biosignals EMG sensor.

Experiment1.sqlite: Entails data from 16 subjects (m/w; Age: 18-30) which conducted biceps curls with a dumbbell following a pre-defined, regular motion pattern until fatigue. sEMG data frequency: 4000Hz

Experiment2.sqlite: Entails data from 13 subjects (m/w; Age: 18-30) which conducted biceps curls with a dumbbell following a pre-defined, irregular motion pattern until fatigue. sEMG data frequency: 4000Hz

Experiment3.sqlite: Entails data from 1 subject (m; Age: 28) which conducted maximum biceps curls with a dumbbell until fatigue. sEMG data frequency: 1000Hz

Each database contains the following features:
- Smoothed relative timestamp (in Seconds)
- sEMG signal
- Smoothed elbow angle (using moving average filter; 0° = fully extended arm)
- Smoothed angle velocity (using moving average filter)
- Signal labels (i.e., if a section of the signal belongs to muscle activation, muscle release, or isometric hold)
- Interpolated elbow angles
- Angle velocity
- Angle acceleration
- Smoothed angle acceleration (using moving average filter)

Example script for reading data (using Python):

from sqlitedict import SqliteDict

db = SqliteDict("experiments.sqlite")
for experiment in db.keys():
    experimentData = db[experiment]
    t_smooth = experimentData[0]
    emg = experimentData[1]
    angleAvg = experimentData[2]
    avgVel = experimentData[3]
    labels = experimentData[4]
    angles_Interpolated = experimentData[5]
    angleVel = experimentData[6]
    angleAcc = experimentData[7]
    avgAcc = experimentData[8]