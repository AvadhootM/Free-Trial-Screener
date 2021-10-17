# Free-Trial-Screener
### Experiment Overview: 
Free Trial Screener At the time of this experiment, Udacity courses currently have two options on the course overview page: "start free trial", and "access course materials". If the student clicks "start free trial", they will be asked to enter their credit card information, and then they will be enrolled in a free trial for the paid version of the course. After 14 days, they will automatically be charged unless they cancel first. If the student clicks "access course materials", they will be able to view the videos and take the quizzes for free, but they will not receive coaching support or a verified certificate, and they will not submit their final project for feedback.   In the experiment, Udacity tested a change where if the student clicked "start free trial", they were asked how much time they had available to devote to the course. If the student indicated 5 or more hours per week, they would be taken through the checkout process as usual. If they indicated fewer than 5 hours per week, a message would appear indicating that Udacity courses usually require a greater time commitment for successful completion, and suggesting that the student might like to access the course materials for free. At this point, the student would have the option to continue enrolling in the free trial, or access the course materials for free instead. 

![exp_screenshot](https://user-images.githubusercontent.com/64949763/137630706-99d29809-9d6f-47d6-b68a-44e0fe4c3674.png)

This screenshot shows what the experiment looks like.   The hypothesis was that this might set clearer expectations for students upfront, thus reducing the number of frustrated students who left the free trial because they didn't have enough time—without significantly reducing the number of students to continue past the free trial and eventually complete the course. If this hypothesis held true, Udacity could improve the overall student experience and improve coaches' capacity to support students who are likely to complete the course.   The unit of diversion is a cookie, although if the student enrolls in the free trial, they are tracked by user-id from that point forward. The same user-id cannot enroll in the free trial twice. For users that do not enroll, their user-id is not tracked in the experiment, even if they were signed in when they visited the course overview page.  

#### Aim of the Experiemnt:  
To improve the overall student experience and improve coaches' capacity to support students who are likely to complete the course.

#### Null Hypothesis:  
This approach might not make a significant change and might not be effective in reducing the early Udacity course cancellation

#### Alternative Hypothesis:  
This might reduce the number of frustrated students who left the free trial because they didn't have enough time, without significantly reducing the number of students to continue past the free trial and eventually complete the course.  


### Experiemnt Design  
The unit of diversion is a cookie here, when a student enrolls in a free trial, their activity is traced by the user_id. Same user_id cannot be enrolled twice, and we are only tracking those students who are enrolled in in a course.

#### Metric Choice:  
##### Invariant Metrics
Invariant metrics are thoses which remain invariant throughout the experiment. One could expect a similar distribution of such metrics both on control and experiment side. In the given experiment, the invariant metrics are as follows -

Number of cookies: That is, number of unique cookies to view the course overview page. This is the unit of diversion and even distribution amongst the control and experiment groups is expected.

Number of clicks: That is, number of unique cookies to click the "Start free trial" button (which happens before the free trial screener is trigger).Equal distribution amongst the experiment and control groups would be expected since at this point in the funnel the experience is the same for all users and therefore elements of the experiment would not be expected to impact clicking the "start free trial" button.

Click-through-probability: That is, number of unique cookies to click the "Start free trial" button divided by number of unique cookies to view the course overview page. Till the time the user clicks the "start free trial" button the user experience is same for all the users. Hence, we expect equal distribution in both the groups.

##### Evaluation Metrics
Evaluation metrics are chosen since there is a possibility of different distribution between experiment and control groups as a function of experiment. Each evaluation metric is associated with a minimum difference (dmin) that must be observed for consideration in the decision to launch the experiment. The ultimate goal is to minimize student frustation and use the limited coaching resources most efficiently. With this in mind, the following conditions must be satisfied -

Increased retension, i.e, the ratio of users who remained enrolled past the 14-day boundary to the number of users to complete checkout should increase.

Decreased gross conversion coupled to increase in net conversion, i.e, less students enrolling in free trial but more students staying beyound the free trial.

Gross conversion: That is, number of user-ids to complete checkout and enroll in the free trial divided by number of unique cookies to click the "Start free trial" button.

Retention: That is, number of user-ids to remain enrolled past the 14-day boundary (and thus make at least one payment) divided by number of user-ids to complete checkout.

Net conversion: That is, number of user-ids to remain enrolled past the 14-day boundary (and thus make at least one payment) divided by the number of unique cookies to click the "Start free trial" button.

Unused Metrics
Number of user-ids: The number of users who enroll in the free trial. User-ids are tracked only after enrolling in the free trial and equal distribution between the control and experimental branches would not be expected. User-id count could be used to evaluate how many enrollments stayed beyond the 14 day free trial boundary, but since it isn't normalized, I have elected not to use it.


### Calculating Standard Deviation
Analytical Estimate of Standard Deviation of Evaluation Metrics  
Standard deviation of Evaluation Metric:
Gross Conversion  = 0.0202
Retention	        = 0.0549
Net Conversion	  = 0.0156  
For each of the metrics the standard deviation is calculated for a sample size of 5000 unique cookies visiting the course overview page. The standard deviation are calculated using the Baseline Values

#### Calculating Number of Pageviews required:  
Page views required for each evaluation metric is calculated separately using the online calculator. The alpha vaue of 0.05 and beta value of 0.2 is used in all the cases.    
Based on the baseline conversion data, Pageviews required is maximum of pageviews required for Gross Conversion, Retention, Net Conversion. Therefore, the required pageviews is 47,41,212.  

#### Calculating the Duration and Exposure of the Experiment:  
If we divert 100% of traffic, given 40,000 page views per day, the experiment would take ~ 119 days. If we eliminate retention, we are left with Gross Conversion and Net Conversion. This reduces the number of required pageviews to 685,325, and an ~ 18 day experiment with 100% diversion and ~ 35 days given 50% diversion.  
A 119 day experiment with 100% diversion of traffic presents both a business risk (potential for: frustrated students, lower conversion and retention, and inefficient use of coaching resources) and an opportunity risk (performing other experiments). However, in general, this is not a risky experiment as the change would not be expected to cause a precipitous drop in enrollment. In terms of timing, an 18 day experiment is more reasonable, but % diversion may be scaled down depending on other experiments of interest to be performed concurrently.


### Analysis:  
Sanity check was performed on invariant metrics in the COntrol group data and Experiment Group Data. We were expecting the equal diversion into the experiment and conterol group. The result is held statisticlaly significant only when the 95% confidance interval does not include zero. From given test, Gross conversion is proved to be Statistically and practically significant. To validate the above test, we perform sign test, which has low sensitivity than the above test.  


### Results:  
Analysis revealed the expected equal distribution of cookies into the control and experimental groups, for the invariant metrics, at the 95% CI. A difference in gross conversion was found to be statistically significant at the 95% CI, and the null hypothesis was rejected. Gross conversion also met the practical significance threshold. Net Conversion was found to be neither statistically nor practically significant at the 95% CI.  
The gols of the experiment was to determine if we filter the students based onteh study time commitment, it would improve the student experience along with the capacity of coaches to support the students without reducing the number of students who enroll after a free trial. We have observed that there was a significant difference in Gross Conversion along with the minute difference in Net Conversion. It shows that decrease in enrollemnt is not related to increase in student enrolling and actually staying in the course after a free trial. Based on this, it makes more sense not to launch this experiment.
