# Create an Alexa Skill



This will be a basic tutorial outlining how to create an alexa skill within the Alexa Development Console and AWS Lambas. 

Begin by creating an Amazon [developer account][l1] and navigate to the Alexa Skill Kit Tab. 

![alt text][img1]

Select **Create Skill**. Enter a project name of your choice. Since we will be learning to build a skill from stracth, select **Custom** as your model type and **Provision your own** as your skill's backend resource. Select **Create Skill**. Then select **Start from scratch** as your template. 

Select **INVOCATION** from the navbar on the left side of the screen and change the invocation name to one of your choice. This serves as the keyword Alexa will use to know you want it to execute this skill. We will use **college bars** for this example. 


Next we need to create intents. These are commands you define that Alexa can execute. In this example, we might define, GetClosingTime. In order for end-users to interact naturally with your intents, you need to define a few different sentence structures for the same comamnd. For example
* What time does \{bar\} close?
* When does  \{bar\} close?
* \{bar\} closing time?

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

Begin by creating an [AWS developer account][l2] and navigate to your developer console. Create a **Lambda** by selecting *resources* from the navbar and selecting **Lambda** under the *services* header. 

![alt text][img5]

In the top right hand corner you should see a geographic location. Due to datacenter limitations, you need to select a region compatable for lamdas. Given our US location, N. Virginia is the best option. Select **Create Function** select *Browse serverless app repository* and select **alexa-skills-kit-nodejs-factskill**. Scroll down, choose a name, e.g. uiucbars, and select **Deploy**.  

This will take a moment.  

Under *resources* select **alexaskillskitnodejsfactskill**. This next part is fairly self explanatory if you are familiar with JavaScript. You can read the template code however we won't be using it.
```js
const GetNewFactHandler = {
    canHandle(handlerInput) {
    const request = handlerInput.requestEnvelope.request;
    return request.type === 'LaunchRequest'
        || (request.type === 'IntentRequest'
        && request.intent.name === 'GetNewFactIntent');
    },
    handle(handlerInput) {
    const factArr = data;
    const factIndex = Math.floor(Math.random() * factArr.length);
    const randomFact = factArr[factIndex];
    const speechOutput = GET_FACT_MESSAGE + randomFact;
    
    return handlerInput.responseBuilder
        .speak(speechOutput)
        .withSimpleCard(SKILL_NAME, randomFact)
        .getResponse();
    },
};
```

At a high level what we are doing is defining an event handler for one or more intents. You can write as many event handelers as you want and it can get complex with state management. The fact skill has two events, `LaunchRequest` and `IntentRequest`. If it returns true then it executes the corresponding method. You define your logic and define a responseBuilder. Given the diversity the the alexa universe, you can define different modal outputs. 
```js
const HelpHandler = {
    canHandle(handlerInput) {
        const request = handlerInput.requestEnvelope.request;
        return request.type === 'IntentRequest'
            && request.intent.name === 'AMAZON.HelpIntent';
},
```
You can also define help intents that allow users to ask alexa for a hint. Despite this, we will be deleting all this code so go ahead and <kbd>command</kbd> + <kbd>a</kbd> or <kbd>control</kbd> + <kbd>a</kbd> and delete the code. 

We will instead use a tool called [ASK-SDK Code Generator][l3]. Navigate back to your Alexa Skill Console and select **JSON Editor** from the navigation bar. Copy and paste the JSON code into the Code Generator and copy the generated code back to your AWS PE.  

![alt text][img6]

We will edit this code later. For now, click **save** to generate the end point address. Above the button cluster you will see **ARN:** \<address\>. Copy that address to your clipboard and navigate back to the Alexa Skill Console. This is the unique identifier for your build. Every resource at amazon is assigned a unique ID. In the Skills Console, select **Endpoint** from the side navbar select **AWS Lambda ARN** paste the address into **default region** and click save endpoints. Select the *test* tab and you can begin testing your skill. 

From here, you can modify the skill and the Lambda and the possibilities from here are pretty limitless. 





[l1]: <https://developer.amazon.com/home.html>
[l2]: <[https://aws.amazon.com/>
[l3]: <http://alexa.codegenerator.s3-website-us-east-1.amazonaws.com/>
[img1]: <img/img1.png>
[img2]: <img/img2.png>
[img3]: <img/img3.png>
[img4]: <img/img4.png>
[img5]: <img/img5.png>
[img6]: <img/img6.png>



