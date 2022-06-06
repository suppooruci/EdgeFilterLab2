# Edge Detection - Systolic Array Design

## Assumptions
1 The following kernel is used as per "Convolution Example" slide (We are filtering with the following kernel - i.e., we don't invert it along x/y before taking dot product). If convolution as opposed to filtering is desired, simply invert the sign.

| 0    | -0.5 | 0  |
|:-----|:-----|:----:|
| **-0.5** | **0**    | **0.5** |
| **0**    | **0.5**  | **0**  |

2. In the above kernel, 0.5 is achieved by ">>" operator

## Schematic 
### Diagram

1. PE_1_1, PE_1_3, PE_2_2, PE_3_1, PE_3_3 are just pipeline cuts  
2. PE_1_2 = element >> 2  
   PE_3_2 = - (element >> 2)  
   PE_2_1 = element >> 2  
   PE_2_3 = - (element >> 2)  
   Above PE's are mirror image of above kernel, because of the direction of flow of input stream  
3. The accumulator sums up all the above PE's in 2.  
4. The select line of mux is as follows  
   
5. The mux chooses 0 for the following   
   
   Otherwise, it chooses accumulated value  
    

### Explanation

## Report
Clock Speed = 
Number of Cycles = 

Code (HwMain.bsv) = 
System Log = 
HW Log = 
