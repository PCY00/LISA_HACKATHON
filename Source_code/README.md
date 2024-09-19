# LISA HACKATHON

## Language Selection

[English](README.md) | [한국어](README_KR.md)

<br><br>

## Data Source
Utilized the anomalous events data from the 2023 LISA Hackathon - `CCAN.txt` file.

<br><br>

## Scale of Data

- The data consists of a total of 2,872,262 entries and 15 columns.

```python
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 2872262 entries, 0 to 2872261
Data columns (total 15 columns):
 #   Column       Dtype  
---  ------       -----  
 0   No           object 
 1   Time_Offset  float64
 2   Type         int64  
 3   ID           object 
 4   Data_Length  int64  
 5   One          object 
 6   Two          object 
 7   Three        object 
 8   Four         object 
 9   Five         object 
 10  Six          object 
 11  Seven        object 
 12  Eight        object 
 13  Unnamed: 13  float64
 14  Unnamed: 14  float64
dtypes: float64(3), int64(2), object(10)
memory usage: 328.7+ MB

```

<br<br>

## Scale of Data

- The data consists of a total of 2,872,262 entries and 15 columns.

<br><br>

## Details and Analysis Results

This data is derived from CAN message communication, and it consists of 15 columns:
- **0th column**: Data number
- **1st column**: Time offset
- **2nd column**: Data type
- **3rd column**: CAN-ID
- **4th column**: Data length
- **5th to 14th columns**: Data fields

By analyzing this data, events can be identified, and abnormal events can be detected.

<br><br>

## Expected Outcomes

- CAN data can improve internal system communication within vehicles and optimize vehicle control systems.
- Vehicle conditions can be monitored to detect issues early and perform maintenance and repairs more efficiently.
- CAN data can be utilized to enhance safety features and implement various systems.
- By analyzing the data, insights into driving habits and road conditions can be gained to improve the safety of both vehicles and drivers.

<br><br>

## Other Deliverables and Explanation

### Data Analysis (Explanation)
1. Through data analysis, abnormal events can be detected (2 points) and analyzed (2 points), leading to a total evaluation score of 4 points.
2. **Detection** refers to identifying combinations of CAN IDs that generate abnormal events and explaining their locations and duration patterns.
3. The cumulative score of all detected and analyzed events will be the total score for the data analysis section.

<br>

### Software Development (Explanation)
1. Through data analysis, abnormal events can be detected (4 points) and analyzed (4 points), leading to a total evaluation score of 8 points.
2. Detection refers to identifying combinations of CAN IDs that generate abnormal events, along with their location and duration patterns.

<br><br>

## Evaluation Criteria and Award Standards
1. **Report**: Focuses on the participants’ ability to detect abnormal events.
2. **Presentation**: Involves explaining the detection of abnormal events.

<br><br>

## Report Structure
- Use of machine learning
- Software development
- Event list
- Event detection and analysis

<br><br>

## Use of Machine Learning

A machine learning model was developed to predict patterns and timings of abnormal events based on data containing only normal events.  
The `OneSVM` model, a type of unsupervised learning model, was adopted. Below is the code and output of the model.

<br>

![image](https://github.com/user-attachments/assets/fe390267-31f8-4d0e-b404-73c679d46858)

<br>

![image](https://github.com/user-attachments/assets/581325ee-6173-4249-927a-a934e2f8a599)

<br><br>

## Software Development

### Real-time CAN Data Collection

- Referenced the example code from the `PCANBasic` library to collect CAN data.
- Applied algorithms for detecting and analyzing abnormal events.
- Once 100 pieces of data are collected, they are stored in a file with a designated name within the `Dataset` directory.
- The algorithm for detecting and analyzing abnormal events was made into a separate file and function, allowing near real-time detection.

<br>

![image](https://github.com/user-attachments/assets/d0208049-de66-46b5-aaf7-5e27d87fd2b6)

<br>

![image](https://github.com/user-attachments/assets/17de31d5-dfb6-40d4-aa29-93b43a21888c)

<br><br>

## Event List

Abnormal events were detected and analyzed based on the following list:

![image](https://github.com/user-attachments/assets/4b5172e7-919c-42e4-9cd2-1f61220a08db)

Event list includes:
- **0316 & 043F**: RPM increases while in P gear
- **0316 & 0440**: RPM is high but speed is 0
- **0316 & 043F**: RPM increases while in N gear
- **0316 & 0440**: Speed increases while in N gear
- **0018 & 043F**: Driver door open while in D gear
- **0018 & 043F**: Driver door open while in R gear
- **0018**: One seatbelt off while eight seatbelt on
- **0018 & 043F**: Belt off while in D gear
- **0018 & 043F**: Belt off while in R gear
- **0018 & 0440**: Belt off while speed increases

<br><br>

## Event Detection and Analysis

All events were detected and analyzed by plotting abnormal events and visually checking if they occur.  
The `time_offset` was used to identify the exact timings of the events. Only the relevant data was extracted and displayed for clarity.

- **0316 & 043F**: RPM increases while in P gear
  - The hexadecimal values were converted to decimal and plotted on a graph, where the blue dot (P gear) shows RPM increasing.

<br>

![image](https://github.com/user-attachments/assets/c3705ada-7670-4fcd-80a5-615e64c5e8dd)

- Extracted all cases where RPM increased while in P gear, and displayed the complete information as shown below.

<br>

![image](https://github.com/user-attachments/assets/13e817ec-361e-4809-a4dd-d54ebc1369d0)

- Selected only the necessary data.

<br>

![image](https://github.com/user-attachments/assets/be080fe4-4e14-46e3-b0de-74193061f550)

- To improve reliability, a graph was generated using `start_time` and `end_time` as variables.

<br>

![image](https://github.com/user-attachments/assets/60c0e3fe-8ed8-4651-ab42-48725d6f696a)

Other events were detected and analyzed using the same approach.
