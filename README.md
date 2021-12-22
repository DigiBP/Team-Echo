# Team Echo <img src="https://static.thenounproject.com/png/27202-200.png" width="50" height="50">
###### Jérôme, Adrian, Michèle, Xi

## Emergency Room Admissions Process <img src="https://cdn.iconscout.com/icon/free/png-256/emergency-call-2199806-1833385.png" width="70" height="70">

1. Patient enters new information into Dialogflow (text-based and voice-assisted chatbot) via our <a href="https://sites.google.com/view/digibp-echo">DigiBP echo website</a> or call our emergency number at +1 732-301-6994 to get help.<br>
![image](https://user-images.githubusercontent.com/89810259/147151458-60c383ac-c848-4ccb-bc40-487b93b74ac1.png)

2. Two integromat scenarios will be triggered on parallel:
<ul>
    <li>Integromat takes the patient information captured on dialogflow and sends the it to <a href="https://docs.google.com/spreadsheets/d/1-ItPmNLtE1ge84TAZbSCsejQhcTdEIR421aFEsS-cC4/edit?usp=sharing">Google Sheet "Callers"</a><br><br>
The Google sheet is then immediately followed by a HTTP module on integromat which triggers the start event on our process modelled on Camunda
<img src="https://user-images.githubusercontent.com/89810259/147152443-8ce25bc0-f2c2-4291-a6ab-6772bece1f76.png"><br><br>
BPMN overview<br>
<image src="https://user-images.githubusercontent.com/89810259/147153929-7b5cdfa0-f219-4b66-8e5f-7cd802a2ac21.png"><br><br>
Start event triggered<br><img src="https://user-images.githubusercontent.com/89810259/147154934-46ae57d9-dbd3-4f88-bc1c-abcf1b3f2daa.png" width="200" height="300"><br><br>
  </li>
    <li>In the meantime, integromat sends the patient data also to <a href="https://www.appsheet.com/start/d8319de6-210c-403e-84ba-f66f587d6f6b">our Emergency Call app</a> (external service named Appsheet was used).<br>
      <image src="https://user-images.githubusercontent.com/89810259/147151496-f2fa04a9-c3b0-4199-a9aa-ebf8e6bac5cf.png" width="650" height="320"><br>
The app has been deployed to Google Play store and can be <a href="https://www.appsheet.com/newshortcut/d8319de6-210c-403e-84ba-f66f587d6f6b">installed on the mobile phone</a> for the paramedic to monitor the real-time status of the callers record. <br>
Once a new patient has called or entered the contact information into dialogflow, the paramedic will get an in-app notification showing: A new callers record is created. <br><br>
User interface on our Emergency Call app:<br><image src="https://user-images.githubusercontent.com/89810259/147155999-e532d869-e31a-40aa-8b3a-b388433b54e1.png", width="500" height="700"><br><br>
        </li>
        </ul>
3. At this point, the paramedics are aware that a new patient needs to be assisted. The emergency call with the patient will be forwarded to an Emergency Call Agent to give first aid instructions. In the meantime, a paramedic will prepare for the dispatch to pick up the patient.<br><image src="https://user-images.githubusercontent.com/89810259/147160442-f98c76ea-73d9-44f4-a911-e33523c95cfc.png" width="650" height="250"><br>

4. Once the dispatch is ready, the paramedic will drive to the patient at the given location and provide first aid to the patient. <br><image src="https://user-images.githubusercontent.com/89810259/147160725-72f3fc56-b517-4a93-9e31-8bda2a024f8a.png" width="150" height="420"><br>


Start integromat scenarios (start process, ping app)
First two roles get triggered in parallel
Emergency call agent -> Roleplay
Prepare for dispatch
Paramedic lane -> DMN (hospital location) -> Give doctor briefing
Briefing (car accident while cycling, injured her legs)
Doctor bring patient to the room
Do check up

Check out our Emergency call chatbot on our [DigiBP echo website](https://sites.google.com/view/digibp-echo) or call our emergency number at +1 732-301-6994 to get help!
<img src="https://i.pinimg.com/originals/0c/67/5a/0c675a8e1061478d2b7b21b330093444.gif" width="80" height="60">


### Links
Google spreadsheet with caller details Dialogflow -> Integromat -> [Google Sheet](https://docs.google.com/spreadsheets/d/1-ItPmNLtE1ge84TAZbSCsejQhcTdEIR421aFEsS-cC4/edit?usp=sharing)

Track the patient info in our [Emergency call app](https://www.appsheet.com/start/d8319de6-210c-403e-84ba-f66f587d6f6b)
