<h1>ExpNo 1 :Developing AI Agent with PEAS Description</h1>
<h3>Name: NAINA MOHAMED Z</h3>
<h3>Register Number:212223230131</h3>


<h3>AIM:</h3>
<br>
<p>To find the PEAS description for the given AI problem and develop an AI agent.</p>
<br>
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

## PROGRAMME:
```
import random


class HealthSensors:
    """Generate simulated readings for a patient in a room."""

    def read_patient(self, room):
        return {
            "heart_rate": random.randint(60, 150),
            "blood_pressure": random.randint(90, 160),
            "temperature": round(random.uniform(36.0, 39.0), 1)
        }


class HealthActuators:
    """Display the action chosen by the agent."""

    def perform_action(self, room, action):
        print(f"Action in Room {room}: {action}")


class HealthMonitoringAgent:
    def __init__(self, sensors, actuators):
        self.sensors = sensors
        self.actuators = actuators
        self.performance = 0

    def choose_action(self, readings):
        alerts = []

        # These thresholds are for this classroom simulation only.
        if readings["heart_rate"] > 110:
            alerts.append("high heart rate")

        if readings["blood_pressure"] > 140:
            alerts.append("high blood pressure")

        if readings["temperature"] > 38.0:
            alerts.append("high temperature")

        if alerts:
            return "Alert healthcare provider: " + ", ".join(alerts)

        return "No alert needed"

    def monitor_room(self, room):
        readings = self.sensors.read_patient(room)

        print(f"\n--- Room {room} ---")
        print(f"Heart rate:     {readings['heart_rate']} bpm")
        print(f"Blood pressure: {readings['blood_pressure']} mmHg")
        print(f"Temperature:    {readings['temperature']} °C")

        action = self.choose_action(readings)
        self.actuators.perform_action(room, action)

        # Score the agent for checking a room.
        self.performance += 1

        # An alert costs one point in this simple performance measure.
        if action != "No alert needed":
            self.performance -= 1

    def run(self, rooms):
        for room in rooms:
            self.monitor_room(room)

        print(f"\nFinal performance score: {self.performance}")


if __name__ == "__main__":
    sensors = HealthSensors()
    actuators = HealthActuators()

    agent = HealthMonitoringAgent(sensors, actuators)
    agent.run(["A", "B"])
```
## OUTPUT:
<img width="1405" height="305" alt="image" src="https://github.com/user-attachments/assets/31f564b6-c7f8-4684-a003-e2e112dc0fda" />
# RESULT:
Thus the Developing AI Agent with PEAS Description was implemented
