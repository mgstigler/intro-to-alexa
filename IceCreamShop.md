In this post, we are building a custom skill called the Ice Cream Shop skill.

Sample Dialogue:

> User: Open Ice Cream Shop

> Alexa: Welcome, you can select from cone or scoop. Which would you like to try?

> User: scoop

> Alexa: Nice, which flavor would you like to get?

> User: I would like strawberry today

> Alexa: You selected strawberry

When a user speaks (Alexa, open ice cream shop) to the Alexa device, the speech is sent to Alexa service where Text to Speech, Speech recognition, Machine Learning, Natural language understanding happens to determine what the user wants, once identified it sends a JSON request to the skill (ice cream shop) which is hosted in Lambda; Once the logic you wrote inside the skill is executed, a JSON response is sent to Alexa service which converts Text to Speech and sent to Alexa device, if the companion Alexa app is used a visual component is displayed on app

### Now that we know how the skill works, let's see what Invocation name, Intents, Utterances and Slots are

### Invocation name:
Name of the skill, what user should say to invoke the skill
ex: Ice Cream Shop

### Intents:
User intention to ask something or do something (action)
ex: Scoop, cone

### Utterances:
Set of phrases user uses when making a request
ex: Alexa, ask ice cream shop for cones
Alexa, ask ice cream shop for flavors in cones

### Slots:
A representative list of possible values
ex: mango, strawberry, caramel, vanilla
let's start creating the skill

1. 
Go to developer.amazon.com/alexa/console/ask

2. Enter credentials and click on Sign in, if you don't have an account, create one.
Developer console will display the skills if any.
3. click create Skill
4. Enter Skill name as ice cream shop, select Default language as English (US) (you can change the language later), by default Custom model will be selected, leave as it is and click on Create Skill

### Intents
To build ice cream shop skill we need three more intents:
- ScoopIntent: To call this intent user can use sentences(utterances) such as “I would like to have a scoop”, “scoop please”,” I will take scoop today”

- coneIntent: To call this intent user can use sentences(utterances) such as “cone please”, “I like a cone”,” I would like to have cone”

- ScoopflavorsIntent: To call this intent user can use sentences(utterances) such as “I like {scoopslot}”, “{scoopslot} please”,” {scoopslot}”.
where {scoopslot} is a Slot name.
{scoopslot} is mapped to Slot Type(scoopslotType) which contains list of possible values such as mango, strawberry, caramel, vanilla

6. Click on add Intents and add ScoopIntent

7. let's add utterances for Scoopintent

8. let's create coneIntent and add utterances

9. Create scoopflavorsIntent, to add slot to the utterances press on open flower bracket, a pop up will open and asks for slot name, enter the slot name-scoopslot

10. Fill all the utterances

>where {scoopslot} is a Slot name.
{scoopslot} is mapped to Slot Type(scoopslotType) which holds a list of possible values such as mango, strawberry, caramel, vanilla
let's create scoopslotType which holds a list of possible values such as mango, strawberry, caramel, vanilla

11. Add Slot Types

12. List all the values for scoopslotType

13. Save the model and link scoopslot to scoopslotType

14. Click on Build Model, you should get Full Build successful message

15. Finally, let's edit our code to reflect handlers for our new intents
Please look over index.js for these changes