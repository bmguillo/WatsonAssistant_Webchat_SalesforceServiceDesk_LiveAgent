# Integrating Watson Assistant Webchat w/ Salesforce ServiceDesk 

In this repo we will illustrate the following usecase: 
- Watson Assistant Webchat integration with SalesForce Service Desk to a Live Agent handoff 

## Terms

We will define a few terms:<br />
User: This will be a customer that will interact via chat(Watson Assistant) to a live agent<br />
SalesForce ServiceCloud: App that helps deliver fast, personalized customer service & improves customer satisfaction to help agents deliver the right answers and service insights<br />
Live Agent: This will be the service desk employee who will interact with SalesForce ServiceCloud to receive chat handoff <br />
Omni-channel:Omni-Channel is a tool that sits inside of either the Sales or Service Console that, once enabled and configured, automatically pushes work to your users in real time. <br />
Routing Configuration:<br />
Queue: Prioritize, distribute, and assign records to teams who share workloads. Queue members can jump in to take ownership of any record in a queue.They're available for chat<br />
QuickFind: search box for Setup pages <br />
Chat Deployment: A deployment is a place on your company’s website that’s enabled for Chat. Create deployments to implement Chat and control its functionality on your website. <br />
Chat Button: Create chat buttons to enable customers to request a chat with an agent directly from your website <br />
Presence Status: Presence statuses indicate whether an agent is online and available to receive incoming work items, or whether the agent is away or offline. You can give users access to presence statuses through profiles. <br />
Service Channel: Customize your service channel settings to define how your organization receives work from various sources, such as chat, email, SOS calls, or social channels <br />


## Setup


### Part 1 - Salesforce Setup & ServiceCloud setup 

- Obtain a Salesforce instance with Administrator access and log in
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/sflogin.png)


- Go to service app
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/serviceapp.png)


- Click on gear and go to service settings
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/setup.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/SalesForceSysAdminProfile.png)

- Ensure ServiceCloud user & chat user is checked on the user profile you are testing with by using QuickFind and searching "users"
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/quickfindusers.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/SalesForceSysAdminProfile.png)


- Enable Omni Channel Settings by utilizing QuickFind
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/omnichannel.png)


- Setup a routing configuration
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/routingconfiguration.png)


- Presence Config(DO NOT HAVE TO CHANGE) shows the max capacity of both cases & chats your agent can handle
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/presenceconfig.png)

- Setup agents available and not available status to external users for chat, you create one per channel per agent
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/presencestatus.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/presencestatus_chat.png)


- Assign chat statuses to an agent(user profile)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/servicepresencestatusesaccess.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/agentchatoptions.png)

- Create a queue, select your routing configuration created previously and objects to be sent to the queue for the agents e.g. chat, cases
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/queue.png)

- OPTIONAL: Add Service Channels(if applicable do for all members of queue for each member profile) e.g. Cases 
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/servicechannels.png)

- Obtain Chat Deployment Code from Deployments to be used to 
  * test the chat functionality in SalesForce 
  * test the Watson Assistant & SalesForce Chat functionality integration
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/deploymentcode.png)

- Create a chat button for code to be generated and embedded into an HTML webpage for your users(you will select your queue created previously & omni-channel
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/chatbuttoncode.png)

### Part 2 - Creation of a HTML Page to test SalesForce Deployment/Chat Button code (transfers to live agent)

 
- Paste both the chat deployment code and chat button code into an empty html file (text/html editor) use an existing website and embed
- Edit the following from the file:  change from <! -- Online Chat Content --> to <"ONLINE"> and <! -- Offline Chat Content --> to <"ONLINE">
- Open in web browser
- Tip: If you are on a mac and want to use textedit, go to format and change to make plain text save it as txt then rename to html for it to display as webpage
- Tip: The agent(user) must set themselves from offline to  "available" in order to receive chats on service console and chat to be available to the external customer
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/setavailablestatus.png)

- Tip: The HTML website chat simulates a customer and the ServiceConsole is the live agent in conversation with them
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/webpagechatonline.png)

- As a customer, click the "online" to initiate a chat with the live agent
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/customerinitiateschat.png)

- Within Service Console, the agent accepts chat by clicking on the checkbox in the omni-channel chat box & a window appears 
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/agentacceptschat.png)


- Agent types & then sends a response to the customer
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/agenttyping.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/agentresponsetocustomer.png)



### Part 3 - Watson Assistant Web Chat setup into your website
- Provision an instance of Watson Assistant Plus

- Create Assistant or Choose Assistant you want to set up the integration with
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/createassistant.png)

- Add integration (on the right)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/addintegration.png)

- Choose Web Chat integration
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/webchatintegration.png)

- Name the integration
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/webchatintegrationname.png)

- Customize UI,Connect SalesForce
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/webchatsalesforcestep1.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/webchatsalesforcestep2.png)

- Turn on Live Agent, create dialog, Create custom labels by going to Data --> Objects and Fields --> Object Manager --> Chat Transcript --> Fields and Relationships, grant the labels to the user profiles
Tip: These should be created before you paste in the code in the next step because the code calls for these
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/transferagentdialog.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/visualforcecustomfields.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/visualforcecustomfields2.png)

- Create a VisualForce page in Salesforce for the chat transcript to be transferred to the agent by replacing SalesForce code: paste from Watson Assistant UI to SalesForce VisualForce Page
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/visualforcepagecreate.png)


### Part 4 - Integration of Watson Assistant virtual agent with SalesForce ServiceCloud Service Console (live agent transfer) Test via Watson Assistant UI and servicecloud and then test your website and service cloud

- Set "available to chat" status in omni-channel window in Service Console as illustrated in Part 2
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/setavailablestatus.png)

- Go to Watson Assistant and select "web chat" and call out to an agent using the intent, you should see a Live Agent Card populate
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/WatsonAssistantwebchattest.png)

- Click request agent (you are simulating a customer)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/WatsonAssistantrequestagent.png)

- Agent accepts chat in SalesForce ServiceCloud by clicking "check mark" to accept in omni-channel window(you are simulating a live agent) and it shows in Watson Assistant
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/SalesForceLiveAgentAcceptchat.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/liveagentjoinschat.png)

- Customer & Live Agent chat & then the agent ends the chat
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/twosidechat.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/endchatsf.png)
![test](https://github.com/bmguillo/WatsonAssistant_Webchat_SalesforceServiceDesk_LiveAgent_AgentAssist/blob/master/img/chatendedwa.png)



#### Resources:
- Deploying Watson Assistant web Chat into your website https://cloud.ibm.com/docs/assistant?topic=assistant-deploy-web-chat, https://cloud.ibm.com/docs/assistant?topic=assistant-deploy-web-chat#deploy-web-chat-extend
- Integrating the Watson Assistant web chat with SalesForce https://cloud.ibm.com/docs/assistant?topic=assistant-deploy-salesforce
- Customer Care Overview Chart: https://www.ibm.com/watson/assets/duo/pdf/184_Onepager_190129_CustomerCareAgentAssist.pdf
- SalesForce integration video: https://www.youtube.com/watch?v=mUx-qvZH-qo
- Watson Agent Assist on ServiceCloud: https://www.youtube.com/watch?v=j5fQAmYPeHs
- Transfer to agent node: https://cloud.ibm.com/docs/assistant?topic=assistant-deploy-web-chat#deploy-web-chat-dialog-prereq


