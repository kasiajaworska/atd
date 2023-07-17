# A dataset for [project name]

Created by Katarzyna Jaworska and Guillaume Rousselet 
at the University of Glasgow
2023-05-09

It contains data collected as part of several experiments:
- [FTTC dataset] EEG data from 120 participants, published before in Rousselet et al. (2009, 2010)
and Bieniek et al. (2013)
- [ATD dataset] EEG data from 48 participants, described before in a PhD thesis (Jaworska, 2017)

## Data and file overview
### [ATD dataset]
N = 48 participants (24 young, 24 older) viewed images of faces, houses and letters intermixed with random noise textures, 
and categorized these images as "face vs. noise", "house vs. noise", or "letter vs. noise" in a block design.
EEG data was collected during each task using Biosemi 128-electrode system sampled at 512 Hz.

Mutual Information (MI) was computed in all participants, at all electrodes and all time points 
between -300 and 998 ms around stimulus onset, for three contrasts:
- face vs. noise trials
- house vs. noise trials
- letter vs. noise trials 

Text files below contain a participants x time points (48 x 650) matrix of maximum MI across electrodes, 
for each of the three contrasts described above.
atd_maxmi_ferp_fnerp.txt [face vs. noise]
atd_maxmi_herp_hnerp.txt [house vs. noise]
atd_maxmi_lerp_lnerp.txt [letter vs. noise]

times.txt contains a vector of 650 time points (-300 to 998 ms around stimulus onset)
age.txt contains ages of all 48 participants
sex.txt contains sex of all 48 participants, where 0 = female | 1 = male

Single-trial EEG data
Electrodes of interest were determined for each participant individually by calculating MI about 
categorical differences: 1) face vs. house, 2) face vs. letter, 3) house vs. letter.
For each of these categorical differences (contrasts), we computed MI at all time points and electrodes. 
We then selected the electrode showing maximum MI for that contrast, in every participant individually.
We finally used this electrode to save single-trial EEG data per participant, containing trials related to the contrast.
As such, the following text files contain time points (650) x trials (variable, max = 100) per condition, per participant,
at the electrode of interest selected using the procedure above.
For example, for the face vs. house contrast, for one young participant, there are four text files:
atd_erp_ferp_herp_f_yp1.txt
atd_erp_ferp_herp_h_yp1.txt
atd_erp_ferp_herp_fn_yp1.txt
atd_erp_ferp_herp_hn_yp1.txt

where
ferp_herp = face vs. house contrast
f = face trials (condition)
h = house trials (condition)
fn = noise trials during "expecting a face" block (condition)
hn = noise trials during "expecting a house" block (condition)
yp1 = young participant 1 
repeated for 24 young and 24 older participants

As such, there are 24 x 2 x 4 = 192 text files containing single-trial EEG data extracted for individual electrode of interest
at the face vs. house contrast. The whole procedure is then repeated for the other two contrasts (face vs. letter, 
house vs. letter) resulting in a total of 576 text files containing single-trial EEG data.
