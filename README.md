# Team Echo <image src="https://static.thenounproject.com/png/27202-200.png" width="50" height="50">
###### Jérôme Branny, Adrian Hadayah, Michèle Curiger, Xi Li

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
      <image src="https://user-images.githubusercontent.com/89810259/147151496-f2fa04a9-c3b0-4199-a9aa-ebf8e6bac5cf.png" width="630" height="320"><br>
The app has been deployed to Google Play store and can be <a href="https://www.appsheet.com/newshortcut/d8319de6-210c-403e-84ba-f66f587d6f6b">installed on the mobile phone</a> for the paramedic to monitor the real-time status of the callers record. <br>
Once a new patient has called or entered the contact information into dialogflow, the paramedic will get an in-app notification showing: A new callers record is created. <br><br>
User interface on our Emergency Call app:<br><image src="https://user-images.githubusercontent.com/89810259/147155999-e532d869-e31a-40aa-8b3a-b388433b54e1.png", width="500" height="700"><br><br>
        </li>
        </ul>
3. At this point, the paramedics are aware that a new patient needs to be assisted. The emergency call with the patient are forwarded to an Emergency Call Agent to give first aid instructions. In the meantime, a paramedic prepares for the dispatch to pick up the patient.<br><image src="https://user-images.githubusercontent.com/89810259/147160442-f98c76ea-73d9-44f4-a911-e33523c95cfc.png" width="920" height="350"><br>

4. Once the dispatch is ready, the paramedic drives to the patient at the given location and provide first aid to the patient. <br><image src="https://user-images.githubusercontent.com/89810259/147165231-130ed01c-ee4e-4b35-b897-16be0c89db90.png" width="380" height="500"><br>

5. Afterwards the paramedic needs to decide which hospital the patient should be brought to: <br><image src="https://user-images.githubusercontent.com/89810259/147165527-d588f69f-8f0a-4f61-8e17-62582049b9ae.png" width="350" height="150"><br>A decision modelling notation (DMN) is used here:<br><image src="https://user-images.githubusercontent.com/89810259/147165851-b39a1aec-5211-46dc-921a-8e109e76b45a.png"><br>
        
6. The patient is then brought to the selected hospital depending on the given canton where the patient is located. The paramedic also gives a briefing of the patient and accident to the doctor. <br><image src="https://user-images.githubusercontent.com/89810259/147166047-1654f09a-77a1-4c12-9f33-b297203fefef.png" width="570" height="150"><br>
        
7. The doctor brings the patient to a room and performs a check up:<br><image src="https://user-images.githubusercontent.com/89810259/147166481-414ff5d5-fb2d-48bd-89cb-0fb244d1d52a.png" width="400" height="680"><br>

8. After the check-up, the doctor needs to decide where the patient should be treated: e.g. if operation or a specialist examination is needed. <br><image src="https://user-images.githubusercontent.com/89810259/147166753-33dfc369-269c-494e-b53c-b76149e8d3d9.png" width="700" height="450"><br>Another DMN is used to choose the treatment location:<image src="https://user-images.githubusercontent.com/89810259/147167913-0ce283db-d960-4c8c-a100-769c5e2a9bb0.png"><br>

9. The End 
        
## Role play for the video recording
<br>
<ul><li>Narrator - Adrian</li>
    <li>Patient - Xi</li>
    <li>Emergency call agent - Michèle</li>
    <li>Paramedic - Jérôme</li>
    <li>Doctor - Michèle</li></ul>
