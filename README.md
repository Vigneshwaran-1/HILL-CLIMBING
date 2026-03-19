<h1>ExpNo 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>Name:  VIGNESHWARAN.P     </h3>
<h3>Register Number: 212224040358   </h3>
<H3>Aim:</H3>
<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>
<h2> Theory: </h2>
<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>


<h2>Algorithm:</h2>
<p>
<ol>
 <li> Evaluate the initial state.If it is a goal state then return it and quit. Otherwise, continue with initial state as current state.</li> 
<li>Loop until a solution is found or there are no new operators left to be applied in current state:
<ul><li>Select an operator that has not yet been applied to the current state and apply it to produce a new state</li>
<li>Evaluate the new state:
  <ul>
<li>if it is a goal state, then return it and quit</li>
<li>if it is not a goal state but better than current state then make new state as current state</li>
<li>if it is not better than current state then continue in the loop</li>
    </ul>
</li>
</ul>
</li>
</ol>

</p>
<hr>
<h3> Steps Applied:</h3>
<h3>Step-1</h3>
<p> Generate Random String of the length equal to the given String</p>
<h3>Step-2</h3>
<p>Mutate the randomized string each character at a time</p>
<h3>Step-3</h3>
<p> Evaluate the fitness function or Heuristic Function</p>
<h3>Step-4:</h3>
<p> Lopp Step -2 and Step-3  until we achieve the score to be Zero to achieve Global Minima.</p>

<hr>
<h2>Sample Input and Output</h2>
<h2>Sample String:</h2> Artificial Intelligence
<h2>Output:</h2>
Score: 643  Solution :  8RzF:oG ]%;CPORRMe!zGvk<br>
Score: 609  Solution :  8RzF:oG ]%;CPqRRMe!zGvk<br>
Score: 604  Solution :  8RzF:oG ]%;CPqRRMe!zGqk<br>
Score: 594  Solution :  8RzF:oG ]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
Score: 551  Solution :  8RzF:oGK]%;CPqRRWe!zGqk<br>
....................................................<br>
..................................................<br>
................................................<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 1  Solution :  Artificial Intelligencf<br>
Score: 0  Solution :  Artificial Intelligence<br>

## PROGRAM
~~~
import random
import string

def random_string(length):
    return ''.join(random.choice(string.ascii_letters + ' ') for _ in range(length))

def fitness(current, target):
    return sum(1 for i in range(len(target)) if current[i] == target[i])

def mutate(current):
    index = random.randint(0, len(current) - 1)
    new_char = random.choice(string.ascii_letters + ' ')
    mutated = list(current)
    mutated[index] = new_char
    return ''.join(mutated)

def hill_climb(target):
    current = random_string(len(target))
    current_score = fitness(current, target)

    iteration = 0

    while current != target:
        neighbor = mutate(current)
        neighbor_score = fitness(neighbor, target)

        if neighbor_score >= current_score:
            current = neighbor
            current_score = neighbor_score

        iteration += 1
        print(f"Iteration {iteration}: {current} (Score: {current_score})")

    print("\nTarget reached:", current)

target = "HELLO WORLD"

hill_climb(target)
~~~
## The output
<img width="460" height="157" alt="image" src="https://github.com/user-attachments/assets/30140a17-2941-49d7-8de9-5f0e8851b427" />


## The result
Thus given experiment is done successfully.


