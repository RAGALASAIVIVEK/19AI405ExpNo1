<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>AIM:</h3>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<h3>Theory</h3>
<h3>Medicine prescribing agent:</h3>
<p>Such this agent prescribes medicine for fever (greater than 98.5 degrees) which we consider here as unhealthy, by the user temperature input, and another environment is rooms in the hospital (two rooms). This agent has to consider two factors one is room location and an unhealthy patient in a random room, the agent has to move from one room to another to check and treat the unhealthy person. The performance of the agent is calculated by incrementing performance and each time after treating in one room again it has to check another room so that the movement causes the agent to reduce its performance. Hence, agents prescribe medicine to unhealthy.</p>
<hr>
<h3>PEAS DESCRIPTION:</h3>
<table>
  <tr>
    <td><strong>Agent Type</strong></td>
    <td><strong>Performance</strong></td>
     <td><strong>Environment</strong></td>
    <td><strong>Actuators</strong></td>
    <td><strong>Sensors</strong></td>
  </tr>
    <tr>
    <td><strong>Medicine prescribing agent</strong></td>
    <td><strong>Treating unhealthy, agent movement</strong></td>
     <td><strong>Rooms, Patient</strong></td>
    <td><strong>Medicine, Treatment</strong></td>
    <td><strong>Location, Temperature of patient</strong></td>
  </tr>
</table>
<hr>
<H3>DESIGN STEPS</H3>
<h3>STEP 1:Identifying the input:</h3>
<p>Temperature from patients, Location.</p>
<h3>STEP 2:Identifying the output:</h3>
<p>Prescribe medicine if the patient in a random has a fever.</p>
<h3>STEP 3:Developing the PEAS description:</h3>
<p>PEAS description is developed by the performance, environment, actuators, and sensors in an agent.</p>
<h3>STEP 4:Implementing the AI agent:</h3>
<p>Treat unhealthy patients in each room. And check for the unhealthy patients in random room</p>
<h3>STEP 5:</h3>
<p>Measure the performance parameters: For each treatment performance incremented, for each movement performance decremented</p>


# DEVELOPED BY : SAI VIVEK
# REG NO: 212223230163
```python

import random
import time

class Patient:
    def __init__(self, room_id):
        # Random temperature between 97 and 102
        self.temperature = round(random.uniform(97.0, 102.0), 1)
        self.room_id = room_id
        self.treated = False

    def is_unhealthy(self):
        return self.temperature > 98.5 and not self.treated

class MedicinePrescribingAgent:
    def __init__(self):
        self.performance = 0
        self.current_room = 0
        self.rooms = [Patient(0), Patient(1)]

    def sense_temperature(self):
        patient = self.rooms[self.current_room]
        print(f"[Room {self.current_room}] Patient temperature: {patient.temperature}°F")
        return patient.temperature

    def treat_patient(self):
        patient = self.rooms[self.current_room]
        if patient.is_unhealthy():
            print(f"[Room {self.current_room}] Patient is unhealthy. Prescribing medicine...")
            patient.treated = True
            self.performance += 1
        else:
            print(f"[Room {self.current_room}] Patient is healthy. No treatment needed.")

    def move_to_next_room(self):
        self.current_room = 1 - self.current_room
        print(f"Moving to room {self.current_room}...")
        self.performance -= 1

    def run(self, cycles=3):
        print("Starting Medicine Prescribing Agent...\n")
        for i in range(cycles):
            print(f"\n--- Cycle {i+1} ---")
            self.sense_temperature()
            self.treat_patient()
            self.move_to_next_room()
            time.sleep(1)

        print(f"\nFinal Performance Score: {self.performance}")

agent = MedicinePrescribingAgent()
agent.run()

```
## OUTPUT :

<img width="1403" height="457" alt="Screenshot 2025-08-19 213302" src="https://github.com/user-attachments/assets/027afa1e-3832-4f2e-89fa-147871da3dab" />

## RESULT :
Thus the Developing AI Agent with PEAS Description was implemented using python programming.

