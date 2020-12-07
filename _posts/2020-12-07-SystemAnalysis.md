---
layout: post
title: System Analysis 
---

# Definitions

## Core-second [cs]
>
Equal to the job which utilizes one core for one second.
> 

example:

For the laptop that what used during experiments the following java code was assumed to be equal 1 S/C.
```java
double r = 1.0;
for (int i = 0; i < 215000; i++) {
   r += 2.0 * RANDOM.nextDouble() - 1.0;
}
```

### Response time for 0.5 [S/C] 

| Statistics | value     |
|------------| ----------|
|count       |  60.000000|
|mean        |   0.501274|
|std         |   0.016998|
|min         |   0.482571|
|25%         |   0.493169|
|50%         |   0.498173|
|75%         |   0.505873|
|max         |   0.616357|

![system anaysis](/images/system_analysis_0_5_core_second.png)


### Response time for 0.9 [S/C]

| Statistics | value     |
|------------| ----------|
|count       | 60.000000 |
|mean        | 0.887082  |
|std         | 0.013601  | 
|min         | 0.834502  |
|25%         | 0.880720  |
|50%         | 0.883032  | 
|75%         | 0.887948  |
|max         | 0.918260  |

![system anaysis](/images/system_analysis_0_9_core_second.png)



### Response time for 1.0 [S/C]

| Statistics | value     |
|------------| ----------|
|count       | 58.000000 |
|mean        | 1.906415  |
|std         | 0.230877  |
|min         | 1.087929  |
|25%         | 1.820376  |
|50%         | 1.901849  |
|75%         | 2.075739  |
|max         | 2.363232  |

![system anaysis](/images/system_analysis_1_0_core_second.png)



### Response time for 1.5 [S/C]

| Statistics | value     |
|------------| ----------|
|count       |31.000000  |
|mean        |17.084434  |
|std         |7.145549   |
|min         |1.959396   |
|25%         |13.926061  |
|50%         |17.469664  |
|75%         |22.194074  |
|max         |28.126784  |

![system anaysis](/images/system_analysis_1_5_core_second.png)

