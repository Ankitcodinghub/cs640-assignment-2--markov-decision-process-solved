# cs640-assignment-2--markov-decision-process-solved
**TO GET THIS SOLUTION VISIT:** [CS640 Assignment 2- Markov Decision Process Solved](https://www.ankitcodinghub.com/product/cs640-homework-4-markov-decision-process-solved/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;91399&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;0&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;0&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;0\/5 - (0 votes)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CS640  Assignment 2- Markov Decision Process Solved&quot;,&quot;width&quot;:&quot;0&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 0px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            <span class="kksr-muted">Rate this product</span>
    </div>
    </div>
<div class="page" title="Page 1">
<div class="section">
<div class="layoutArea">
<div class="column">
4: Markov Decision Process

In this assignment, you are asked to implement value iteration and policy iteration. We provide a script of skeleton code. Your tasks are the following.

1. Implement the algorithms following the instruction. 2. Run experiments and produce results.

Do not modify the existing code, especially the variable names and function headers. Submission

Everything you need to complete for this assignment is in this notebook. Once you finish, please save this file as PDF and submit it via Gradescope. Make sure the outputs are saved when you create the PDF file!

Collaboration

You must complete this assignment independently, but feel free to ask questions on Piazza. In particular, any questions that reveal your answers must be made private.

Packages

The package(s) imported in the following block should be sufficient for this assignment, but you are free to add more if necessary. However, keep in mind that you should not import and use any MDP package. If you have concern about an addition package, please contact us via Piazza.

In [ ]:

</div>
</div>
<div class="section">
<div class="layoutArea">
<div class="column">
import numpy as np import sys

np.random.seed(4) # for reproducibility

</div>
</div>
</div>
<div class="layoutArea">
<div class="column">
Examples for testing

</div>
</div>
</div>
</div>
<div class="page" title="Page 2">
<div class="layoutArea">
<div class="column">
The following block contains two examples used to test your code. You can create more for debugging, but please add it to a different block.

</div>
</div>
<div class="section">
<div class="layoutArea">
<div class="column">
# a small MDP

states = [0, 1, 2]

actions = [0, 1] # 0 : stay, 1 : jump jump_probabilities = np.matrix([[0.1, 0.2, 0.7],

<pre>                                [0.5, 0, 0.5],
                                [0.6, 0.4, 0]])
</pre>
for i in range(len(states)):

jump_probabilities[i, :] /= jump_probabilities[i, :].sum()

rewards_stay = np.array([0, 8, 5]) rewards_jump = np.matrix([[-5, 5, 7], [2, -4, 0],

[-3, 3, -3]])

T = np.zeros((len(states), len(actions), len(states))) R = np.zeros((len(states), len(actions), len(states))) for s in states:

T[s, 0, s], R[s, 0, s] = 1, rewards_stay[s]

T[s, 1, :], R[s, 1, :] = jump_probabilities[s, :], rewards_jump[s, :]

example_1 = (states, actions, T, R)

# a larger MDP

states = [0, 1, 2, 3, 4, 5, 6, 7]

actions = [0, 1, 2, 3, 4]

T = np.zeros((len(states), len(actions), len(states))) R = np.zeros((len(states), len(actions), len(states))) for a in actions:

T[:, a, :] = np.random.uniform(0, 10, (len(states), len(states))) for s in states:

T[s, a, :] /= T[s, a, :].sum()

R[:, a, :] = np.random.uniform(-10, 10, (len(states), len(states)))

example_2 = (states, actions, T, R)

</div>
</div>
</div>
<div class="layoutArea">
<div class="column">
In [ ]:

</div>
</div>
<div class="layoutArea">
<div class="column">
Value iteration

Implement value iteration by finishing the following function, and then run the cell.

</div>
</div>
<div class="layoutArea">
<div class="column">
In [ ]:

</div>
<div class="column">
def value_iteration(states, actions, T, R, gamma = 0.1, tolerance = 1e-2, max_steps = 100):

</div>
</div>
</div>
<div class="page" title="Page 3">
<div class="section">
<div class="layoutArea">
<div class="column">
Vs = [] # all state values Vs.append(np.zeros(len(states))) # initial state values steps, convergent = 0, False

Q_values = np.zeros((len(states),len(actions)))

while not convergent:

########################################################################

# TO DO: compute state values, and append it to the list Vs

# V_(k+1) = max_a sum_(next state s’) T[s,a,s’] * (R[s,a,s’] + gamma * V-k(s)) V_next = np.zeros(len(states))

for s in states:

V_next[s] = -sys.maxsize for a in actions:

Q_value = 0

for s_ in states:

Q_value += T[s,a,s_] * (R[s,a,s_] + gamma * Vs[-1][s]) V_next[s] = max(V_next[s],Q_value)

Q_values[s,a] = Q_value

Vs.append(V_next)

############################ End of your code ########################## steps += 1

convergent = np.linalg.norm(Vs[-1] – Vs[-2]) &lt; tolerance or steps &gt;= max_steps

<pre>    ########################################################################
    # TO DO: extract policy and name it "policy" to return
    # Vs should be optimal
    # the corresponding policy should also be the optimal one
</pre>
policy = np.argmax(Q_values,axis=1)

############################ End of your code ########################## return Vs, policy, steps

print(“Example MDP 1”)

states, actions, T, R = example_1

gamma, tolerance, max_steps = 0.1, 1e-2, 100

Vs, policy, steps = value_iteration(states, actions, T, R, gamma, tolerance, max_steps) for i in range(steps):

print(“Step ” + str(i)) print(“state values: ” + str(Vs[i])) print()

print(“Optimal policy: ” + str(policy)) print()

print()

print(“Example MDP 2”)

states, actions, T, R = example_2

gamma, tolerance, max_steps = 0.1, 1e-2, 100

</div>
</div>
</div>
</div>
<div class="page" title="Page 4">
<div class="section">
<div class="layoutArea">
<div class="column">
Vs, policy, steps = value_iteration(states, actions, T, R, gamma, tolerance, max_steps) for i in range(steps):

print(“Step ” + str(i)) print(“state values: ” + str(Vs[i])) print()

print(“Optimal policy: ” + str(policy))

</div>
</div>
</div>
<div class="layoutArea">
<div class="column">
<pre>Example MDP 1
Step 0
state values: [0. 0. 0.]
</pre>
<pre>Step 1
state values: [5.4 8.  5. ]
</pre>
<pre>Step 2
state values: [5.94 8.8  5.5 ]
</pre>
<pre>Step 3
state values: [5.994 8.88  5.55 ]
</pre>
<pre>Step 4
state values: [5.9994 8.888  5.555 ]
</pre>
<pre>Optimal policy: [1 0 0]
</pre>
<pre>Example MDP 2
Step 0
state values: [0. 0. 0. 0. 0. 0. 0. 0.]
</pre>
<pre>Step 1
state values: [2.23688505 2.67355205 2.18175138 4.3596377  3.41342719 2.97145478
</pre>
<pre> 2.60531101 4.61040891]
</pre>
<pre>Step 2
state values: [2.46057355 2.94090725 2.39992652 4.79560147 3.75476991 3.26860026
</pre>
<pre> 2.86584211 5.0714498 ]
</pre>
<pre>Step 3
state values: [2.4829424  2.96764277 2.42174403 4.83919785 3.78890418 3.2983148
</pre>
<pre> 2.89189522 5.11755389]
Optimal policy: [0 2 0 3 3 3 2 3]
</pre>
</div>
</div>
</div>
<div class="page" title="Page 5">
<div class="layoutArea">
<div class="column">
Policy iteration

Implement policy iteration by finishing the following function, and then run the cell.

In [ ]:

</div>
</div>
<div class="section">
<div class="layoutArea">
<div class="column">
def policy_iteration(states, actions, T, R, gamma = 0.1, tolerance = 1e-2, max_steps = 100): policy_list = [] # all policies explored

initial_policy = np.array([np.random.choice(actions) for s in states]) # random policy policy_list.append(initial_policy)

Vs = [] # all state values

Vs = [np.zeros(len(states))] # initial state values steps, convergent = 0, False

while not convergent:

########################################################################

# TO DO:

# 1. Evaluate the current policy, and append the state values to the list Vs

# V[policy_i][k+1][s] = sum_(s_) T[s,policy_i[s],s_] * ( R[s,policy_i[s],s_ + gamma * V[policy_i][k][s_] ) V_next = np.zeros(len(states))

for s in states: tmp = 0

for s_ in states:

tmp += T[s,policy_list[-1][s],s_] * ( R[s,policy_list[-1][s],s_] + gamma * Vs[-1][s_] )

V_next[s] = tmp

Vs.append(V_next)

# 2. Extract the new policy, and append the new policy to the list policy_list

# policy_list[i+1][s] = argmax_(a) sum_(s_) T[s,a,s_] * ( R[s,a,s_] + gamma * Vs[s_] ) policy_new = np.array([np.random.choice(actions) for s in states])

for s in states:

new_tmp = np.zeros((len(actions))) for a in actions:

sum = 0

for s_ in states:

sum += T[s,a,s_] * ( R[s,a,s_] + gamma * Vs[-1][s_] ) new_tmp[a] = sum

policy_new[s] = np.argmax(new_tmp)

policy_list.append(policy_new)

############################ End of your code ########################## steps += 1

convergent = (policy_list[-1] == policy_list[-2]).all() or steps &gt;= max_steps

return Vs, policy_list, steps print(“Example MDP 1”)

</div>
</div>
</div>
</div>
<div class="page" title="Page 6">
<div class="section">
<div class="layoutArea">
<div class="column">
states, actions, T, R = example_1

gamma, tolerance, max_steps = 0.1, 1e-2, 100

Vs, policy_list, steps = policy_iteration(states, actions, T, R, gamma, tolerance, max_steps) for i in range(steps):

print(“Step ” + str(i))

print(“state values: ” + str(Vs[i])) print(“policy: ” + str(policy_list[i])) print()

print()

print(“Example MDP 2”)

states, actions, T, R = example_2

gamma, tolerance, max_steps = 0.1, 1e-2, 100

Vs, policy_list, steps = policy_iteration(states, actions, T, R, gamma, tolerance, max_steps) for i in range(steps):

print(“Step ” + str(i))

print(“state values: ” + str(Vs[i])) print(“policy: ” + str(policy_list[i])) print()

</div>
</div>
</div>
<div class="layoutArea">
<div class="column">
<pre>Example MDP 1
Step 0
state values: [0. 0. 0.]
policy: [0 1 1]
</pre>
</div>
</div>
<div class="layoutArea">
<div class="column">
<pre>Step 1
state values: [ 0.
policy: [1 0 0]
</pre>
</div>
<div class="column">
1. -0.6]

</div>
</div>
<div class="layoutArea">
<div class="column">
<pre> Example MDP 2
 Step 0
 state values: [0. 0. 0. 0. 0. 0. 0. 0.]
 policy: [3 2 1 4 3 3 4 0]
</pre>
<pre> Step 1
 state values: [ 1.79546043  2.67355205 -0.08665637 -4.92536024  3.41342719  2.97145478
</pre>
<pre>  -1.69624246  2.48967841]
 policy: [0 2 0 3 3 3 2 3]
</pre>
More testing

The following block tests both of your implementations. Simply run the cell.

</div>
</div>
</div>
<div class="page" title="Page 7">
<div class="section">
<div class="layoutArea">
<div class="column">
steps_list_vi, steps_list_pi = [], [] for i in range(20):

states = [j for j in range(np.random.randint(5, 30))]

actions = [j for j in range(np.random.randint(2, states[-1]))] T = np.zeros((len(states), len(actions), len(states)))

R = np.zeros((len(states), len(actions), len(states)))

for a in actions:

T[:, a, :] = np.random.uniform(0, 10, (len(states), len(states))) for s in states:

T[s, a, :] /= T[s, a, :].sum()

R[:, a, :] = np.random.uniform(-10, 10, (len(states), len(states)))

Vs, policy, steps_v = value_iteration(states, actions, T, R)

Vs, policy_list, steps_p = policy_iteration(states, actions, T, R) steps_list_vi.append(steps_v)

steps_list_pi.append(steps_p)

print(“Numbers of steps in value iteration: ” + str(steps_list_vi)) print(“Numbers of steps in policy iteration: ” + str(steps_list_pi))

</div>
</div>
</div>
<div class="layoutArea">
<div class="column">
In [ ]:

</div>
</div>
<div class="layoutArea">
<div class="column">
<pre>Numbers of steps in value iteration: [4, 4, 5, 4, 5, 5, 5, 4, 4, 4, 5, 5, 4, 5, 5, 4, 5, 4, 5, 5]
Numbers of steps in policy iteration: [2, 2, 2, 2, 2, 3, 2, 3, 2, 2, 2, 2, 3, 2, 2, 3, 2, 2, 2, 2]
</pre>
</div>
</div>
</div>
