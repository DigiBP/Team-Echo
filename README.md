# Team Echo <image src="https://static.thenounproject.com/png/27202-200.png" width="50" height="50">
###### Jérôme Branny, Adrian Hadayah, Michèle Curiger, Xi Li

## Emergency Room Admissions Process <img src="https://cdn.iconscout.com/icon/free/png-256/emergency-call-2199806-1833385.png" width="70" height="70">

1. Patient enters new information into Dialogflow (text-based and voice-assisted chatbot) via our <a href="https://sites.google.com/view/digibp-echo">DigiBP echo website</a> or by calling our emergency number on +1 732-301-6994 to get help.<br><br>
![image](https://user-images.githubusercontent.com/89810259/147151458-60c383ac-c848-4ccb-bc40-487b93b74ac1.png)<br>
Our website was built using [Google Sites](https://sites.google.com/). The chatbot was integrated into the website with a few lines of code which can be viewed in our GitHub repository here.
    
2. Two Integromat scenarios are triggered **in parallel**:
<ul>
    <li>Integromat takes the patient information captured from Google DialogFlow and sends it to <a href="https://docs.google.com/spreadsheets/d/1-ItPmNLtE1ge84TAZbSCsejQhcTdEIR421aFEsS-cC4/edit?usp=sharing">Google Sheet "Callers"</a><br><br>
The Google sheet is then immediately followed by a HTTP module on Integromat which triggers the start event in our process modelled in Camunda.<br><br>
<img src="https://user-images.githubusercontent.com/89810259/147152443-8ce25bc0-f2c2-4291-a6ab-6772bece1f76.png"><br><br>
Dialogflow<br><image src="https://user-images.githubusercontent.com/89810259/147171597-70f61728-5ae5-4817-a1d9-932d9afd273d.png"><br><br>
A Google Sheet named "Callers" is used to store the patient records:<br> <image src="https://user-images.githubusercontent.com/89810259/147171719-01cc3a6f-1dc1-4345-ad04-ceaf6d364a0d.png"><br><br>
BPMN overview<br>
<image src="https://user-images.githubusercontent.com/89810259/147153929-7b5cdfa0-f219-4b66-8e5f-7cd802a2ac21.png"><br><br>
Start event triggered:<br><br><img src="https://user-images.githubusercontent.com/89810259/147154934-46ae57d9-dbd3-4f88-bc1c-abcf1b3f2daa.png" width="200" height="300"><br><br>
  </li>
    <li>In parallel, Integromat sends the same patient data to <a href="https://www.appsheet.com/start/d8319de6-210c-403e-84ba-f66f587d6f6b"> our Emergency Manager app</a> (an external service named Appsheet was used).<br>
      <image src="https://user-images.githubusercontent.com/89810259/147151496-f2fa04a9-c3b0-4199-a9aa-ebf8e6bac5cf.png" width="630" height="320"><br><br>
Appsheet transforms our Google Sheet "Callers" to an user-friendly data-monitoring platform with a modern user interface. <br><br>
          The app has been deployed to the Google Play store and can be <a href="https://www.appsheet.com/newshortcut/d8319de6-210c-403e-84ba-f66f587d6f6b">installed on the mobile phone</a> for the paramedic to monitor the real-time status of the incoming callers records. <br><br>
Once a new patient has called or entered the contact information into DialogFlow, the paramedic will get an in-app notification showing: <em>"A new caller's record is created."</em> <br><br>
User interface of our Emergency Manager app (iPad view):<br><br>Overview of the caller's info sorted by descending date:<br><image src="https://user-images.githubusercontent.com/89810259/147155999-e532d869-e31a-40aa-8b3a-b388433b54e1.png" width="500" height="700"><br><br>
          Choose the "Map" function to view the location of all callers:<br>
          <image src="https://user-images.githubusercontent.com/89810259/147265813-9881de7b-c034-41d1-a4da-89c60c4b1a3b.png" width="500" height="700"><br><br>
              Tap on the "Schedule" function to display a daily, weekly or monthly view of the callers records:<br><image src="https://user-images.githubusercontent.com/89810259/147266660-2cb0bf81-8aea-42ff-b0bd-f9a81a3aa50e.png" width="500" height="700"><br><br>
              Tap on the patient record to view patient contact details:<br><image src="https://user-images.githubusercontent.com/89810259/149843756-7cef214c-7af3-4563-aaaf-1099b6984baf.png" width="500" height="700"><br><br>          
              It is also possible to manually add a new patient record or update an existing record:<br><image src="https://user-images.githubusercontent.com/89810259/149843524-0cc09aba-4496-4217-a60a-ffaeee758303.png" width="500" height="700"><br>
        </li>
        </ul>
3. At this point, upon the in-app notification, the paramedics are immediately aware that a new patient needs to be assisted. The emergency call with patient data are forwarded to an Emergency Call Agent to give first aid instructions. Meanwhile, a paramedic prepares for dispatch to pick up the patient:<br><image src="https://user-images.githubusercontent.com/89810259/147160442-f98c76ea-73d9-44f4-a911-e33523c95cfc.png" width="920" height="350"><br>

4. Once the dispatch is ready, the paramedic drives to the patient's location and provides any necessary first aid:<br><image src="https://user-images.githubusercontent.com/89810259/147165231-130ed01c-ee4e-4b35-b897-16be0c89db90.png" width="380" height="500"><br>

5. Afterwards, the paramedic has to decide which hospital the patient should be brought to: <br><image src="https://user-images.githubusercontent.com/89810259/147165527-d588f69f-8f0a-4f61-8e17-62582049b9ae.png" width="350" height="150"><br>A decision modelling notation (DMN) is used here:<br><image src="https://user-images.githubusercontent.com/89810259/147165851-b39a1aec-5211-46dc-921a-8e109e76b45a.png"><br>
        
6. The patient is then brought to the selected hospital depending on the given canton where the patient is located. The paramedic also gives a patient and accident briefing to the doctor:<br><image src="https://user-images.githubusercontent.com/89810259/147166047-1654f09a-77a1-4c12-9f33-b297203fefef.png" width="570" height="150"><br>
        
7. The doctor brings the patient to a room and performs a check up:<br><image src="https://user-images.githubusercontent.com/89810259/147166481-414ff5d5-fb2d-48bd-89cb-0fb244d1d52a.png" width="400" height="680"><br>

8. After the check-up, the doctor will decide where the patient should be treated (for example, if a specialist examination or an operation is needed): <br><image src="https://user-images.githubusercontent.com/89810259/147166753-33dfc369-269c-494e-b53c-b76149e8d3d9.png" width="700" height="450"><br>Another DMN is used to choose the treatment location:<br><image src="https://user-images.githubusercontent.com/89810259/147167913-0ce283db-d960-4c8c-a100-769c5e2a9bb0.png"><br>

9. The patient is directed to the selected treatment location and will get treated.
        
## Roles played in the video recording
<ul><li>Narrator - Adrian</li>
    <li>Patient - Xi</li>
    <li>Emergency call agent - Michèle</li>
    <li>Paramedic - Jérôme</li>
    <li>Doctor - Michèle</li></ul>

Watch our recorded Team Echo video on [Microsoft Teams](https://fhnw365.sharepoint.com/:v:/r/teams/AS21_MSc_MI_DigiBP_M365-5TeamEcho/Freigegebene%20Dokumente/5%EF%B8%8F%E2%83%A3%20Team%20Echo/Video/Team_Echo_Video.mp4?csf=1&web=1&e=jWX15j) or on [SWITCHTube](https://tube.switch.ch/videos/NBbokyjVC6)

## Links 
[DigiBP-Echo website](https://sites.google.com/view/digibp-echo)<br>
[Google sheet "Callers"](https://docs.google.com/spreadsheets/d/1-ItPmNLtE1ge84TAZbSCsejQhcTdEIR421aFEsS-cC4/edit#gid=0)<br>
[App "Emergency Manager"](https://www.appsheet.com/start/d8319de6-210c-403e-84ba-f66f587d6f6b)<br>
[Dialogflow](https://dialogflow.cloud.google.com/#/agent/emergency-call-qhun/intents)<br>
[Integromat](https://www.integromat.com)<br>
[DigiBP classroom instance](https://digibp.herokuapp.com/camunda/app/welcome/default/#!/login)
