# ETCI-2021-Competition-on-Flood-Detection
Notebook for submission using fast.ai

Link: https://nasa-impact.github.io/etci2021/

The Challenge
The flood event detection contest, organized by the NASA Interagency Implementation and Advanced Concepts Team in collaboration with the IEEE GRSS Earth Science Informatics Technical Committee, seeks to develop approaches to delineate open water flood areas as an effort to identify flood extent, an impactful disaster that occurs frequently throughout the world. The competition involves a supervised learning task—participants will develop algorithms to identify flood pixels after training their algorithm against a training set of synthetic aperture radar (SAR) images. Participants are required to submit binary classification maps, and performance will be evaluated using the intersection over union (IOU) score.

Competition Phases
competition_flow

This challenge aims to promote innovation in the detection of flood events and water bodies, as well as to provide objective and fair comparisons among methods. The ranking is based on quantitative accuracy parameters computed with respect to undisclosed test samples. Participants will be given a limited time to submit their segmentation maps after the competition starts. The contest will consist of two phases:

Phase 1 (Development): Participants are provided with training data (which includes reference data) and validation data (without reference data until phase 1 concludes) to train and validate their algorithms. Participants can submit prediction results for the validation set to the codalab competition website to get feedback on the performance from April 15 to May 14, 2021. The performance of the best submission from each account will be displayed on the leaderboard.

Phase 2 (Test): Participants receive the validation set reference data for model tuning and test data set (without the corresponding reference data) to generate predictions and submit their binary classification maps in numpy array format from May 15 to June 30, 2021. After evaluation of the results, three winners will be announced on July 1, 2021.

The Data
The contest dataset is composed of 66,810 (33,405 x 2 VV & VH polarization) tiles of 256×256 pixels, distributed respectively across the training, validation and test sets as follows: 33,405, 10,400, and 12,348 tiles for each polarization. Each tile includes 3 RGB channels which have been converted by tiling 54 labeled GeoTIFF files generated from Sentinel-1 C-band synthetic aperture radar (SAR) imagery data using Hybrid Pluggable Processing Pipeline “hyp3”. Training tiles correspond to intensity values for VV and VH polarization with the following attributes.

File name prefix: <region>_<datetime>*_x-*_y-*_<vv | vh>.png
Size : 5.3 GB (uint8)
Number of images : 66,810
Acquisition mode : Interferometric Wide Swath
Native resolution : 5x20m
User guide : link
Semantic Labels
The provided training data is split across 29 root folders named <region>_<datetime>*, region being the region and datetime being the date and time of the flood event. Each root folder includes 4 sub-folders: vv, vh, flood_label and water_body_label with 2,068 files each. vv and vh correspond to the satellite images listed earlier and images in the flood_label and water_body_label folder provide reference ground truth.

Please note that the labeling has been performed as follows: The Hybrid Pluggable Processing Pipeline, “hyp3” system takes the Sentinel archive and creates a set of processes to get to a consistent method of generating the VV/VH amplitude or power imagery. The imagery is then converted to a 0 - 255 grayscale image. Total of 54 labeled GeoTIFF files from regions converted into tiles:

Nebraska (1,741 sq. km.)
North Alabama (13,789 sq. km.)
Bangladesh (7,150 sq. km.) in
Red River North (6,746 sq. km.)
Florence (7,197 sq. km.)
Each TIFF is converted to multiple 256x256 tiles (scenes) The reference ground truth file is 256×256 pixels large. The pixel values (0 or 1) correspond to the two following classes:

For flood labels:
0: Flood not present
1: Flood present
For water body labels:
0: Land
1: Water body
Visual examples of the training data and the high-resolution segmentation map used in the contest are shown in Figure 1.

(a) Sentinel-1 image (Grayscale: VV)	(b) Sentinel-1 image (Grayscale: VH)	(c) Reference flood data (Grayscale)	(d) Reference water body data (Grayscale)
(a) Sentinel-1 image (Grayscale: VV)	(b) Sentinel-1 image (Grayscale: VH)	(c) Reference flood data (Grayscale)	(d) Reference water body data (Grayscale)
Figure 1: Visual examples of satellite images (a), (b) and reference data (c) and (d) used in ETCI 2021.

We expect participants to provide a binary segmentation of the region of interest (ROI), (i.e. 256x256 pixels) as a numpy arra with the byte (uint8) data type:

1: Flood region
0: Not flood region
The reference data for the validation remain undisclosed until phase 1 concludes howeveer reference data for the test set remains undisclosed and will be used for the evaluation of the results.

Results:
The first, second, third, and fourth-ranked teams in the ECTI competition will be declared as winners.
  
The code posted here is heavily inspired from https://medium.com/cloud-to-street/jumpstart-your-machine-learning-satellite-competition-submission-2443b40d0a5a
