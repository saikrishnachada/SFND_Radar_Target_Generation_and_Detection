# **Project : Radar Target Generation and Detection** 

### Implementation steps for the 2D CFAR process  

Important concept to understand before diving into CFAR is 'False Alarm Rate'. It is a measure of the presence of radar target when there is no valid target present. To keep the false alarm rate lower without missing the valid targets we use a technique called as CFAR (Constant False Alarm Rate), by varying the detection threshold based on the target surroundings. A CIFAR process includes a sliding of a window across the cells after the Fast Fourier Transformation (FFT) is performed on the radar signal data. The process loops across the cells and decides the presence of targets based on the noise estimate. This CFAR technique can be applied to both 1D and 2D data.

#### 2D CIFAR:
-	The 2D CFAR is implemented in both dimensions of the range doppler block. It involves the training cells occupying the cells surrounding the cell under test (CUT) with a guard grid in between to prevent the impact of a target signal on the noise estimate as shown below.
<img src= https://github.com/saikrishnachada/SFND_Radar_Target_Generation_and_Detection/blob/master/Images/2D_CFAR.png>
---

### Selection of Training, Guard cells and offset  
Size of Training cells in range dimension (Tr) = 10  
Size of Training cells in doppler dimension (Td) = 8  
Size of Guard cells in range dimension (Gr) = 4  
Size of Guard cells in doppler dimension (Gd) = 4  
Offset = 1.2  

---

### Steps taken to suppress the non-thresholded cells at the edges
The process above will generate a thresholded block, which is smaller than the Range Doppler Map as the CUT cannot be located at the edges of matrix. Hence,few cells will not be thresholded. To keep the map size same the set those values to 0.

```python
RDM(RDM~=0 & RDM~=1) = 0;
```
---

### Results
1. Range Measurement
<img src= https://github.com/saikrishnachada/SFND_Radar_Target_Generation_and_Detection/blob/master/Images/1st_FFT_range_plot.jpg>
2. Range Doppler Response
<img src= https://github.com/saikrishnachada/SFND_Radar_Target_Generation_and_Detection/blob/master/Images/Range_doppler_response.jpg>
2. 2D CFAR Implementation
<img src= https://github.com/saikrishnachada/SFND_Radar_Target_Generation_and_Detection/blob/master/Images/2D_CFAR_Implementation.jpg>
