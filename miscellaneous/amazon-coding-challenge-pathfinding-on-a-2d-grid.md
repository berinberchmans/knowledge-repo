---
description: Bright Network Internship Task 1
---

# Amazon Coding Challenge -Pathfinding on a 2D Grid

## Bright Network Internship Task 1 - Amazon Coding Challenge

**Overview:**

In this challenge, you are going to implement Amazon's pathfinding algorithm for Amazon's self-driving delivery vehicles. The self-driving vehicle will need to create a path on a 2D-grid that contains a starting point (x,y), a delivery point (x,y) and a number of obstacles. Your vehicle can navigate to any of the adjacent squares (even diagonally), as long as the squares are inbound and do not contain an obstacle.

**General notes:**

You can use any language and ideally the output is to a command line.

**Phase 1:**

Implement a 10x10 grid that contains a starting point on (9,0), the delivery point on (9,9) and the following obstacles on locations (9,7) (8,7) (6,7) (6,8).

Your algorithm should calculate a valid path avoiding the obstacles and reaching the delivery point.

Your solution should print the path in the format of \[(x1,y2), (x2,y2)....] and also the number of steps.

**Phase 2:**

Add an additional 20 randomly placed obstacles and print their location using the format \[(x1,y1),(x2,y2)...]. The obstacles should not overlap existing ones and should not be places at the start and delivery points. Your algorithm should calculate a valid path avoiding the obstacles and reaching the delivery point.

Your solution should print the path in the format of

\[(x1,y2), (x2,y2)....]

**Bonus:**

In the event that your vehicle is unable to reach its destination, your algorithm should print “Unable to reach delivery point" and identify which obstacles to be removed in order for the vehicle to reach its destination.

Your algorithm should suggest the least amount of obstacles using the format \[(x1,y1),(x2,y2)...)] in order for your vehicle to reach its destination.

### Solution

{% embed url="https://github.com/berinberchmans/amazon_coding_challenge.git" %}
The code for the task can be found in the above repository
{% endembed %}

#### 1️⃣ Phase 1

To create a pathfinding algorithms for Amazon’s self-driving delivery vehicles, I propose a solution to find the 2D path between the starting point and delivery point by framing the problem as a **MDP or Markov Decision Process**. In MDP, an agent is supposed to decide the best action to select based on his current state. This step is taken on each state the agent is in. An MDP has states, actions and rewards. The states here are the cells of the grid. The actions are the set of all possible actions the delivery car can take, here it is \[UP, DOWN, LEFT, RIGHT, TOP-LEFT, TOP-RIGHT, BOTTOM-LEFT, BOTTOM-RIGHT] . The rewards are values that it gets for moving to a particular state. I created a 10x10 grid and then created the transition table and reward table for the problem. I assigned a reward value of 5 for the delivery point and -3 for the obstacles. Using value-iteration we can get a set of values for each cell of the grid. These values can be used to map the ideal route the delivery car can take to reach the delivery point.

Having generated the ideal route, I have represented this route on the grip graphically as follows :-

The path, obstacles and delivery point are represented as the following colors:-

🟨 - The path for delivery

🟦 - The obstacles

🟩 - Delivery Point

![](../.gitbook/assets/Figure\_10.png)

The output of the algorithms is as follows (starting from initial cell to the cell right before delivery) :-

```python
[[0, 0], [1, 1], [2, 2], [3, 3], [4, 4], [5, 5], [6, 6], [7, 7], [8, 8]]
No of Steps : 9
```

#### 2️⃣ Phase 2

In phase 2, I increased the number of obstacles to 20. The obstacles are randomly generated. It can be seen that the algorithm find the optimal route with just a small increase in the number of steps. The following are two different runs with the same number of obstacles.

**Run 1 :**

![](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/0bd8cb30-59bd-461f-9f74-b1d864e1fd4a/Figure\_1.png?X-Amz-Algorithm=AWS4-HMAC-SHA256\&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD\&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220721%2Fus-west-2%2Fs3%2Faws4\_request\&X-Amz-Date=20220721T155238Z\&X-Amz-Expires=86400\&X-Amz-Signature=71c792b7c6c802965d7f875dddd5e42916bc708857e802c269c30babfddd535a\&X-Amz-SignedHeaders=host\&response-content-disposition=filename%20%3D%22Figure\_1.png%22\&x-id=GetObject)

```python
[[0, 0], [1, 1], [2, 2], [2, 3], [2, 4], [3, 5], [4, 6], [5, 7], [5, 8], [6, 9], [7, 9], [8, 9]]
No of Steps : 12
```

**Run 2 :**

![](<../.gitbook/assets/222 (1).png>)

```python
[[0, 0], [1, 0], [2, 1], [3, 2], [4, 3], [5, 4], [6, 5], [7, 6], [7, 7], [8, 8]]
No of Steps : 10
```

For a third run, I am increased the number of obstacles to 30. It can be seen that the algorithm still preforms well as it reaches the delivery point with almost the same number of steps as the previous cases.

![](<../.gitbook/assets/fig 3- 30 obs.png>)

```python
[[0, 0], [0, 1], [1, 2], [1, 3], [2, 4], [3, 5], [4, 5], [5, 6], [6, 6], [7, 7], [7, 8], [8, 9]]
No of Steps : 12
```

#### 🅱️ Bonus

In the case that the delivery point is blocked off, I print out that the delivery wasn’t possible.&#x20;

```python
Could not deliver
```
