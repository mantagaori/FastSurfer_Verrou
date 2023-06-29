# FastSurfer_Verrou

This project is submitted as part of Concordia University's COMP490 - Computer Science Project I course's final report.
<br><br>
The project aims to study the numerical uncertainty of FastSurfer's whole-brain segmentation pipeline. <br><br>
To assess the numerical uncertainty of the FastSurfer’s segmentation model, its standard performance is compared with its performance after a random noise has been introduced into the model. 
Verrou, a Valgrind-based tool, and its float-point random rounding operations is used to reduce the precision of the segmentation model’s computations. 
The impact of reduced precision on the performance of FastSurfer’s segmentation pipeline will be used to provide insights into the deep-learning model’s reliability and its limitations if any.
<br><br>Please refer to the <i>Report.ipynb</i> file for details relevant to the experiment and results.

