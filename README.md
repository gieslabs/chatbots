# How to create an alexa skill



This will be a basic tutorial outlining how to create an alexa skill within the Alexa Development Console and AWS Lambas. 

Begin by creating an Amazon [developer account][l1] and navigate to the Alexa Skill Kit Tab. 

![alt text][img1]

Select **Create Skill**. Enter a project name of your choice. Since we will be learning to build a skill from stracth, select **Custom** as your model type and **Provision your own** as your skill's backend resource. Select **Create Skill**. Then select **Start from scratch** as your template. 

Select **INVOCATION** from the navbar on the left side of the screen and change the invocation name to one of your choice. This serves as the keyword Alexa will use to know you want it to execute this skill. We will use **college bars** for this example. 


Next we need to create intents. These are commands you define that Alexa can execute. In this example, we might define, GetClosingTime. In order for end-users to interact naturally with your intents, you need to define a few different sentence structures for the same comamnd. For example
* "What time does \{bar\} close?"
* "When does  \{bar\} close?"
* " \{bar\} closing time?"

![alt text][img2]

Using curly braces will define a variable, this variable is specified by the user. Below your sentances you'll see a section **Intent Slots**. Since you've defined your variable bar, you then need to define it as a slot type. 

Select the plus sign in the side navbar next to **Slot Types (0)** and name it *BAR* and input the name of all the bars on campus. 
* brothers
* murphys
* legends
* the hub
* joes
* kams
* lion

![alt text][img3]

I choose the colloquial name of each bar; however, to make the skill more robust, add nicknames for each e.g. brothers ~ bros, lion ~ red lion etc. Navigate back to BarClosingTime and change the slot type for **bar** to the *BAR* slot you just created. 

![alt text][img4]

You have built the front end of your Alexa skill per-say. Select build and check that your skill compiles correctly. You could technically use this skill however, we need to satisfy the backend requirement. You have two options: an AWS lambda endpoint or your own HTTP endpoint. For ease of use, we will specify an AWS lambda endpoint. 

Begin by creating an [AWS developer account][https://aws.amazon.com/] and navigate to your developer console. Create a **Lambda** by selecting *resources* from the navbar and selecting **Lambda** under the *services* header. 

![alt text][img5]

In the top right hand corner you should see a geographic location. Due to datacenter limitations, you need to select a region compatable for lamdas. Given our US location, N. Virginia is the best option. Select **Create Function** select *Browse serverless app repository* and select **alexa-skills-kit-nodejs-factskill**. Scroll down, choose a name, e.g. uiucbars, and select **Deploy**.  

![alt text][img6]

This will take a moment.  

Under *resources* select **alexaskillskitnodejsfactskill** 



[l1]: <https://developer.amazon.com/home.html>
[img1]: <img/img1.png>
[img2]: <img/img2.png>
[img3]: <img/img3.png>
[img4]: <img/img4.png>
[img5]: <img/img5.png>
[img6]: <img/img6.png>


