# How to create an alexa skill

This will be a basic tutorial outlining how to create an alexa skill within the Alexa Development Console and AWS Lambas. 

Begin by creating an Amazon [developer account][l1] and navigate to the Alexa Skill Kit Tab. 

![alt text][img1]

Select **Create Skill**. Enter a project name of your choice. Since we will be learning to build a skill from stracth, select **Custom** as your model type and **Provision your own** as your skill's backend resource. Select **Create Skill**. Then select **Start from scratch** as your template. 

Select **INVOCATION** from the navbar on the left side of the screen and change the invocation name to one of your choice. This serves as the keyword Alexa will use to know you want it to execute this skill. We will use **college bars** for this example. 


Next we need to create intents. These are commands you define that Alexa can execute. In this example, we might define, GetClosingTime. In order for end-users to interact naturally with your intents, you need to define a few different sentence structures for the same comamnd. For example
    - "What time does \{bar\} close?"
    - "When does  \{bar\} close?"
    - " \{bar\} closing time?"

![alt text][img2]

Using curly braces will define a variable, this variable is specified by the user. Below your sentances you'll see a section **Intent Slots**. Since you've defined your variable bar, you then need to define it as a slot type. 

Select the plus sign in the side navbar next to **Slot Types (0)**

[l1]: <https://developer.amazon.com/home.html>
[img1]: <img/img1.png>
[img2]: <img/img2.png>

