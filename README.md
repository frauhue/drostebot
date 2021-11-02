# drostebot
Models for the AI of the chatbot-widget of Droste-Hülshoff Burg


## Local testing

To get the assistant up and running for experimentation on your local machine, you need to run two servers:
The action server:
`rasa run actions `

And the actual assistant server:
`rasa shell --enable-api`

The `shell` command allows you to interact with the assistant directly on the command line.


To run tests, just run
`rasa test`

If there are any actions in your test stories, again make sure, that the action server is running.

## 'Training' the assistant
The relevant files to "breathe life into" the bot are:
    - `domain.yml`
     This is where all the intents and actions need to be declared and the responses defined.
     Remember that all response names must start with "utter_"
    - `data/nlu.yml`
      This is the place for the "training data" i.e. a hierarchical list of intent names with the respective examples in the child nodes.
      These are required to allow the bot to recognize e.g. different types of greetings.
      To get started, about 10-20 examples per intent should be enough. It is a good idea not to overthink this in the beginning and adapt these later according to user feedback (e.g. if a certain type     of    greeting is never recognised)
    - `data/rules.yml`
      Rules are hard constraints on certain cases in interaction that override any other behaviour. These are used if e.g. we want to guarantee that a goodbye is always answered with a goodbye.
      Rules should be used with care, the fewer the better. As always, for more information refer to the documentation.
      
    - `data/stories.yml`
      Stories are the bigger picture of conversations where we define the paths of the conversation. This is a complex topic, so please refer to the docs: https://rasa.com/docs/rasa/writing-stories  
    
    - `tests`
      This is obviously where the conversation tests go. Writing enough test stories is very important, as it saves a lot of time compared to testing the bot manually.
