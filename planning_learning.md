UNIT 3: Planning and Learning

AI systems must do two things:

Plan → Decide what actions to take.
Learn → Improve performance from experience.
PART A: PLANNING
What is Planning in AI?

Planning is the process of determining a sequence of actions that transforms an initial state into a goal state.

General Structure
Initial State → Actions → Goal State
Example

Problem:

You are in Delhi and want to reach Mumbai.

Plan:

Delhi
 ↓
Book Ticket
 ↓
Travel
 ↓
Mumbai

AI generates these actions automatically.

1. Blocks World

Blocks World is the most famous planning problem in AI.

It consists of:

Blocks
Table
Robot Arm

The robot can:

Pick up a block
Put down a block
Stack blocks
Unstack blocks
Example

Initial State

A
B

C

Goal State

A
B
C

The AI must determine the sequence of moves required.

Why Blocks World?

It helps researchers study:

Planning
Reasoning
Problem Solving

without real-world complexity.

Components of a Planning System

A planning system generally contains:

1. Initial State

Current situation.

Example:

Block A on Block B
2. Goal State

Desired situation.

Example:

Block B on Block C
3. Actions/Operators

Possible moves.

Examples:

PickUp(A)
PutDown(A)
Stack(A,B)
4. Planner

Generates a sequence of actions.

5. Execution System

Executes generated plan.

Diagram
Initial State
      ↓
   Planner
      ↓
 Action Plan
      ↓
 Execution
      ↓
 Goal State
2. Goal Stack Planning

One of the earliest AI planning methods.

Uses:

Stack Data Structure (LIFO)

Idea

Break a goal into smaller sub-goals.

Store them in a stack.

Solve topmost goal first.

Example

Goal:

A on B
B on C

Stack:

A on B
B on C

Solve:

B on C

first.

Then:

A on B
Advantages

✔ Simple

✔ Easy implementation

Disadvantages

✘ Poor for complex planning

✘ Cannot handle uncertainty well

3. Nonlinear Planning

Also called Partial Order Planning.

Unlike linear planning, actions need not follow one fixed sequence.

Linear Planning
A → B → C → D

Only one order.

Nonlinear Planning
A
↙ ↘
B   C
 ↘ ↙
  D

B and C can occur in any order.

Example

Preparing Tea

Tasks:

Boil water
Get cup

Can happen simultaneously.

Advantages

✔ Flexible

✔ Efficient

✔ Supports parallel activities

4. Hierarchical Planning

Breaks a large problem into smaller sub-problems.

Example

Goal:

Organize College Event

Subgoals:

Book Hall
Arrange Food
Invite Guests
Manage Registration

Each subgoal is further divided.

Hierarchical Tree
Event
├── Hall
├── Food
├── Guests
└── Registration
Advantages

✔ Reduces complexity

✔ Easier planning

5. Conditional Planning

Used when outcomes are uncertain.

Plan depends on conditions.

Example
IF raining
    Carry Umbrella
ELSE
    Go Normally
Decision Tree
          Weather
          /     \
      Rainy     Sunny
        |         |
 Umbrella      Normal
Applications
Robotics
Autonomous vehicles
Decision support systems
6. Planning Problem

A planning problem generally consists of:

Initial State

Current situation.

Goal State

Desired outcome.

Actions

Possible operations.

Constraints

Restrictions.

Example

Robot Navigation

Initial:

Room A

Goal:

Room D

Actions:

Move(A,B)
Move(B,C)
Move(C,D)
7. Analysis of Planning Approaches
Approach	Advantage	Limitation
Goal Stack	Simple	Not scalable
Nonlinear	Flexible	Complex
Hierarchical	Efficient	Requires decomposition
Conditional	Handles uncertainty	Larger search space
PART B: LEARNING

Learning is the ability of an AI system to improve performance through experience.

What is Learning?

Learning means:

Experience → Knowledge → Better Performance
Human Example

Child touches hot object.

Learns:

Hot object = Danger

Future behavior improves.

Different Learning Approaches

Major learning methods:

Supervised Learning
Unsupervised Learning
Reinforcement Learning
Inductive Learning
1. Supervised Learning

Learning using labeled data.

Structure
Input + Correct Output

AI learns mapping.

Example

Spam Detection

Training Data:

Email → Spam
Email → Not Spam

AI learns patterns.

Applications
Disease prediction
Face recognition
Sentiment analysis
Advantages

✔ High accuracy

✔ Easy evaluation

Disadvantages

✘ Requires labeled data

2. Unsupervised Learning

No labels provided.

AI discovers patterns itself.

Example

Customer Segmentation

AI groups customers based on behavior.

Common Tasks
Clustering
Pattern discovery
Dimensionality reduction
Applications
Market analysis
Recommendation systems
Advantages

✔ No labeling needed

Disadvantages

✘ Results may be difficult to interpret

3. Reinforcement Learning (RL)

Learning through rewards and penalties.

Inspired by human learning.

Components
Agent

Learner.

Environment

World.

Action

Move chosen.

Reward

Feedback.

Example

Game Playing

Good Move → +10
Bad Move → -10

Agent learns best strategy.

RL Cycle
Agent
  ↓
Action
  ↓
Environment
  ↓
Reward
  ↓
Agent
Applications
Self-driving cars
Robotics
AlphaGo
Resource optimization
4. Inductive Learning

Learning general rules from specific examples.

Example

Observed:

Dog 1 barks
Dog 2 barks
Dog 3 barks

Conclusion:

Dogs bark
Characteristics

✔ Generalization

✔ Knowledge discovery

Machine Learning Tasks

Common ML tasks include:

1. Classification

Predict categories.

Examples:

Spam / Not Spam
Fraud / Genuine
Diseased / Healthy
Example
Email → Spam

Output is a class.

2. Regression (important though not explicitly listed)

Predict numerical values.

Examples:

House prices
Temperature prediction
3. Clustering

Group similar objects.

Example:

Customers

into different groups.

Simple Statistical-Based Learning

Uses statistics to identify patterns.

Methods include:

Mean
Median
Probability
Correlation
Example

Student Marks

Average = 75

AI uses statistical measures to learn trends.

Perceptron

Perceptron is the simplest Artificial Neural Network.

It mimics a biological neuron.

1. Single Layer Perceptron (SLP)

Structure:

Inputs
  ↓
Weights
  ↓
Summation
  ↓
Output
Mathematical Model

y=f(∑
i=1
n
	​

w
i
	​

x
i
	​

+b)

Where:

x = inputs
w = weights
b = bias
f = activation function
Example

Email Spam Detection

Output:

Spam
or
Not Spam
Limitation

Cannot solve complex nonlinear problems.

2. Multi-Layer Perceptron (MLP)

Contains multiple hidden layers.

Structure:

Input Layer
      ↓
Hidden Layer
      ↓
Hidden Layer
      ↓
Output Layer
Advantages

✔ Learns complex patterns

✔ High accuracy

✔ Foundation of Deep Learning

Applications
Image recognition
Speech recognition
NLP
Medical diagnosis
Difference Between Single Layer and Multi-Layer Perceptron
Feature	Single Layer	Multi Layer
Hidden Layers	No	Yes
Complexity	Low	High
Accuracy	Lower	Higher
Nonlinear Problems	No	Yes
Deep Learning	No	Yes
