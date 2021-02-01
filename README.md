# Classification of people wearing face masks vs not wearing face masks

## Literature Review

The daily new COVID-19 cases in October showed a trend of rebounding across United States. According to New York Times' report, the daily average of new COVID-19 cases this past week has topped 71,000, a 40 percent increase from the average 2 weeks ago. [1] Why this surge happened is hard to explain but it is time to emphasize the Covid-19 prevention again. Due to the reopening, the probability of virus spread increases as people are exposed to each other. When someone have to go to public places, the simple ways to avoid infection are to keep 6- feet social distance, wear masks and wash hands often.[2] Mask is proved to be an effective barrier to prevent respiratory droplets from spreading into the air when social distance is hard to maintain or when people are within an enclosed spaces that had inadequate ventilation.  [3] In order to flatten the curve, thirty-three states have required people to wear masks in indoor public spaces, such as restaurants and stores. [4] For some places, the implementation of this mandates still relied on the manual supervision of the staffs and personal consciousness of the residents. In this way, employees are actually exposed to the risk of COVID-19 infection. Automation would be a better choice when sensitive outside activities are not preferred during the pandemic.[5] Automation is the application of technology, programs, robotics or processes to achieve outcomes with minimal human input, which perfectly satisfy the social distance requirement. Employees could work remotely and avoid cross infection.[6] Besides, faced with crushing demands during the pandemic, enterprises started considering automation to maintain operation without close contact of employees and lower the costs by combining hyper automation technologies with redesigned operational processes. [7] Thus, automated mask detection is truly an appropriate technique to support the mask mandate.  

Computer vision is one of the core technologies to implement the mask detection. It is a technique to make computers "see" and gain high-level understanding of the content of digital images like photographs and videos. [8] And it has contributed to the diagnose, prevention and control as well as clinical management in the fight of COVID-19.[9] Take thermal detection as an example, Infrared thermography could help pre-screen potential virus carries at ports of entry.[10] China has applied this as one of screening processes to avoid cases imported from overseas. Thus, it’s also practical for public places to apply mask detection and support the control of COVID-19. 

Mask detection includes two steps: face detector and mask/ no mask classifier. [11] Our research focus on developing precise mask/ no mask classification model. 


## Results and Discussion
**Accuracy and Complexity Analysis**

Below is the table showing general performance of each model: 

|Model|Discription| Train_Accuracy/% |Test_Accuracy/%|Time_Consuming/s|
|:----:|:----:|:----:| :----: |:----:|
|1|baseline|50|50|\|
|2|basic|93|87|668|
|3|pre-train|100|95|2791|

As we can see, 
* CNN model can classify images better than the baseline model.

* The pre-train model will greatly improve the accuracy of classification. However, the time it consuming is far more than the one basic CNN model costs.The reason is that pre-train model is more complicated than basic one, including more conolutional layers and more dimensions, which means it requires training a large amount of parameters. 

**Overfitting Issue**
* For our baisc model, though there are fluctuations in train accuracy and test accuracy curves, which is common during this process, the trend shows that the basic model is not much overfitting.
* As for pre-train model, while there are the same fluctuations as the basic one, the downward continuous trend of last epoches imply that our pre-train model seems to be overfitting. The reason why this happened might be the training accuracy of our model is so high, which is 100%, that the overfitting phenomenon comes out.

**Businees Value**

Now we demonstrate that CNN is really helpful for companies or governments to scan people's faces to know if they are wearing masks. Our model can accelerate scanning process using the power of the computers and can help save much material and human resource.

However, companies and governments ought to think about the balance between accuracy and complexity when they are training models. The higher the accuracy we want, the more time the process will consume due to the complexity. The issue is more problematic when we want to update the model when we find new images or features. Also, the volume of our sample is not as large as the sample in real life companies and governments will use. As the size of the sample enlarges, the computational complexity will rise in geometric or even exponential form, and finally result in "disaster" such as gradient explosion. As a result, the baclance between accuracy and complexity is of essential importance to the users of CNN image classification model.

## Conclusion

*   Download data from web. Use ImageDataGenerator to read the image data that store in our google drive. We have a train_generator, test_generator that contain information of train and test images. 

*   Firstly, we build a CNN model that only use 20 epochs because we want the model to run fast. However, the accuarcy of the model is not good. In this case, we assume that the model do not have enough epochs to train the model. Increased the epochs to 50 and add earlystop. Interstingly, we got a decent result with 87% of accuracy. However, we want to apply pre-train model to see if it has better performance.

*   In second model, we import VGG16 and frozen four blocks and only keep 5th block. Declared a new model and train this model with same train and test data. The accuracy of thie model achieve 95%. Which is pretty impressed.

*   When we apply ImageDataGenerator to make test_generator for predtiction result, we have to set shuffle = FALSE, so that the image and label can match properly.

*   Our model solve our business problem very well by accuractely distinguish that people wearing or no wearing mask.

## Reference

[1] Here Are the States Where COVID-19 Is Increasing

https://www.healthline.com/health-news/here-are-the-states-where-covid-19-is-increasing

[2] How COVID-19 Spreads
https://www.cdc.gov/coronavirus/2019-ncov/prevent-getting-sick/how-covid-spreads.html

[3] Considerations for Wearing Masks
https://www.cdc.gov/coronavirus/2019-ncov/prevent-getting-sick/cloth-face-cover-guidance.html

[4] State-by-State Guide to Face Mask Requirements
https://www.aarp.org/health/healthy-living/info-2020/states-mask-mandates-coronavirus.html

[5] The power of automation during COVID-19
https://www.dxc.technology/au/ds/148526/148661-the_power_of_automation_during_covid_19

[6] What is automation?
https://www.ibm.com/topics/automation

[7] COVID-19 accelerates enterprise use of automation in digital transformation
https://www.cio.com/article/3562697/covid-19-accelerates-enterprise-use-of-automation-in-digital-transformation.html

[8] A Gentle Introduction to Computer Vision
https://machinelearningmastery.com/what-is-computer-vision/

[9] COVID-19 Control by Computer Vision Approaches: A Survey
Ulhaq, A., Born, J., Khan, A., Gomes, D., Chakraborty, S., & Paul, M. (2020). COVID-19 Control by Computer Vision Approaches: A Survey. IEEE Access.

[10] Thermal Detection: How Computer Vision Could Help Curve the Coronavirus Pandemic
https://www.computer.org/publications/tech-news/covid19-research/thermal-detection

[11] A practical solution to real-world face mask detection – Part 1
https://neuralet.com/article/real-time-face-mask-detection-part-one/#Problem_statement
