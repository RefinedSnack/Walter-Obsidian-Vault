---  
share: "true"  
---  
# Mini-Project 1  
  
# Group Members  
- Walter DeGering  
  
# Implemented Algorithm Description  
  
I used a weighted sum for the attractive and repulsive force. The attractive force pulls the robot towards the goal. The repulsive force pushes the robot away from the direction of the obstacles. This one is proportional to the inverse of the distance.  
  
```python  
def attractiveForce(robotPos, goalPos, distanceSensors, alpha):  
    angle = math.atan2(goalPos[1] - robotPos[1], goalPos[0] - robotPos[0])  
    force_x = alpha * math.cos(angle)  
    force_y = alpha * math.sin(angle)  
    return force_x, force_y  
  
    
  
def repulsiveForce(sensor_angle, distance, beta):  
    if distance == 0.0:  
        distance = 0.1  
    repulsive_force_x = beta * (1 / distance) * math.cos(sensor_angle)  
    repulsive_force_y = beta * (1 / distance) * math.sin(sensor_angle)  
    return repulsive_force_x, repulsive_force_y  
  
    
  
def computeTrajectory(robotPos, goalPos, distanceSensors):  
    alpha = 1.0  
    beta = 3.0  
    total_force_x, total_force_y = 0.0, 0.0  
    attractive_force_x, attractive_force_y = attractiveForce(robotPos, goalPos, distanceSensors, alpha)  
    total_force_x += attractive_force_x  
    total_force_y += attractive_force_y  
    for i, distance in enumerate(distanceSensors):  
  
        sensor_angle = math.radians(robotPos[2] + i * 360 / len(distanceSensors))  
        repulsive_force_x, repulsive_force_y = repulsiveForce(sensor_angle, distance, beta)  
        total_force_x += repulsive_force_x  
        total_force_y += repulsive_force_y  
    trajectory = normalize([total_force_x, total_force_y])  
    return trajectory  
```  
  
# Experimentation and Challenges  
- Attempted to adjust the parameters (alpha and beta) to find an optimal balance between attraction and repulsion. We needed to up beta  
- I initially tried to apply the attractive force proportional to distance, however this was too much, so I removed the term  
  
# Navigation Performance  
- It worked fairly well, but got stuck on corners of shapes  
- World 1: Failed  
- World 2: Worked  
- World 3: Worked  
- World 4: Failed  
  
# Experience Highlights  
- The algorithm successfully navigated through simple environments. And avoided obstacles   
- Balancing attractive and repulsive forces proved challenging, requiring fine-tuning of parameters.  
- Handling edge cases, such as zero-distance sensor readings, required additional consideration.  
