# Edge Detection - Systolic Array Design

## Assumptions
1 The following kernel is used as per "Convolution Example" slide (We are filtering with the following kernel - i.e., we don't invert it along x/y before taking the dot product). If convolution as opposed to filtering is desired, simply invert the signs.

| **0**    | **-0.5** | **0**  |
|:-----|:-----|:----:|
| **-0.5** | **0**    | **0.5** |  
| **0**    | **0.5**  | **0**  |

2. In the above kernel, 0.5 is achieved by ">>" operator

## Schematic 
### Diagram
![Schematic Diagram](https://user-images.githubusercontent.com/92354970/172226013-7c185566-cbe7-4bad-9d75-f872657a6cac.png)

### Explanation
1. PE_1_1, PE_1_3, PE_2_2, PE_3_1, PE_3_3 are just pipeline cuts  
2. PE_1_2 = element >> 2  
   PE_3_2 = - (element >> 2)  
   PE_2_1 = element >> 2  
   PE_2_3 = - (element >> 2)  
   Above PE's are mirror image of above kernel, because of the direction of flow of input stream  
3. The accumulator sums up all the above PE's in 2.  
4. Start row_count and column_count when PE_2_2 gets input data. 
5. The mux chooses 0 for the following   
   -- Whenever row_count == 0 OR column_count == 0  
   Otherwise,   
   -- it chooses the accumulated value    
   When pixOutCnt exceeds image size, stop enqueing to tx line.  
    

## Report
Clock Speed =   
Number of Cycles =   

Base Folder: home/suppoor/CS250B/lab2/   (on rivendell)  
Code (HwMain.bsv) =  ulx3s_bsv/projects/image_proc/HwMain.bsv   
System Log = ulx3s_bsv/projects/image_proc/system.log  
HW Log =   ulx3s_bsv/projects/image_proc/hw.log  
