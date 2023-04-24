# CSDS 133 Written Homework 3
**Instructions:** Each question is worth 10 points unless otherwise stated. Write your answers below the question. Only one answer is needed from a group unless otherwise specified. Each answer should be formatted so it renders properly on github. **Answers that do not render properly may not be graded.** Each person in each group must commit and push their own work. You will not get credit for work committed/pushed by someone else even if done by you. Each person is expected to do an approximately equal share of the work, as shown by the git logs. **If we do not see evidence of equal contribution from the logs for someone, their individual grade will be reduced substantially.** Please comment the last commit with "FINAL COMMIT" and **enter the final commit ID in canvas by the due date.**

Note: Questions which ask you to "prove" something often require a general argument rather than specific examples. For other questions, please show your work rather than just the final answer for full credit.

1. Suppose $A \cup B$ denotes an event containing all atomic events in either $A$ or $B$ or both, and $A \cap B$ denotes an event containing only atomic events in both $A$ and $B$. Using the axioms of probability, show that $\Pr(A\cup B)=\Pr(A)+\Pr(B)-\Pr(A\cap B)$. Explain why this matches our intuitive analogy of probability-as-area.

Answer:
$Pr(A \cup B) = Pr(A \cup (B \setminus A))$

$= Pr(A) + Pr(B \setminus A)$ (mutually exclusive, Axiom 3)

$= Pr(A) + Pr(B \setminus A) + Pr(A \cap B) - Pr(A \cap B)$
(Adding $0 = Pr(A \cap B) - Pr(A \cap B)$ )

$= Pr(A) + Pr((B \setminus A) \cup (A \cap B)) - Pr(A \cap B)$
(mutually exclusive, Axiom 3)

$= Pr(A) + Pr(B) - Pr(A \cap B)$

It matches the area intuition because when we add Pr(A) to Pr(B), then the overlapping area would be added twice. So we need to eliminate the overlapping area once, which is $Pr(A \cup B)$.

2. Explain why it would not violate the axioms of probability for someone to have degrees of beliefs $\Pr(A)=0.4$, $\Pr(B)=0.3$ and $\Pr(A \cup B)=0.5$ for two events $A$ and $B$. 

Answer:\
Based on the axioms of probability, the probability of two events is equal to the sum of probability of the first event and the probability of the second event if these two events are mutually disjoint, and probability of any event is between 0 and 1. However, A and B are not necessarily the mutually disjoint events. In other words, there exists some atomic event that are in both A and B, and $\Pr(A \cap B)$ is higher than 0. In this scenario, $\Pr(A \cap B)=\Pr(A) + \Pr(B) - \Pr(A \cup B)$ while $\Pr(A \cap B)$ is higher than 0, so $\Pr(A) + \Pr(B)$ can be higher than $\Pr(A \cup B)$. Moreover, $\Pr(A)$, $\Pr(B)$, and $\Pr(A \cup B)$ are all between 0 and 1. Therefore, the given scenario would not violate the axioms of probability.

3. If someone had the degrees of belief in question 2 above, what are the possible degrees of belief they might assign to $\Pr(A \cap B)$ without violating the axioms of probability?

Answer:\
Due to what we proved in Q1., we have:  
$Pr(A \cup B) = Pr(A) + Pr(B) - Pr(A \cap B)$   
Then, $Pr(A \cap B) = Pr(A) + Pr(B) - Pr(A \cup B)= 0.4 + 0.3 - 0.5 = 0.2$

4.	A disease D has two symptoms, pain and fever. Pain occurs in 95% of the people with D, but also in 10% of the people without D. Fever occurs in 90% of the people with D, but also in 5% of the people without D. D affects 1% of people. Which of pain or fever is a better indicator of D? 

Answer: 

Let A be the people having pain; let B be the people having fever.\
Let $C$ be the people having disease D.\
Probability that a person has pain is $\Pr(A)=\Pr(A \cap C) + \Pr(A \cap \bar{C})=\Pr(A|C) \times \Pr(C)+\Pr(A| \bar{C}) \times \Pr(\bar{ C})=(95\%) \times (1\%)+(10\%) \times (100\% - 1\%)=0.1085$\
Probability that a person has fever is $\Pr(B)=\Pr(B \cap C) + \Pr(B \cap \bar{C})=\Pr(B | C) \times \Pr(C)+\Pr(B | \bar{C}) \times \Pr(\bar{C})=(90\%) \times (1\%)+(5\%) \times (100\% - 1\%)=0.0585$\
Probability that a person has disease D given that this person has pain is $\Pr(C|A)=\frac{\Pr(A|C) \times \Pr(C)}{\Pr(A)}=\frac{(95\%) \times (1\%)}{0.1085}=\frac{19}{217} \approx 0.088$\
Probability that a person has disease D given that this person has fever is $\Pr(C|B)=\frac{\Pr(B|C) \times \Pr(C)}{\Pr(B)}=\frac{(90\%) \times (1\%)}{0.0585}=\frac{2}{13} \approx 0.154$\
Therefore, $\Pr(C|B)$ is higher than $\Pr(C|A)$, so fever is a better indicator of D.

5.  An exam consists of multiple choice questions, each with six choices. A student has a degree of belief 0.8 they will know the answer to a question. If they do not, they intend to pick one of the six choices at random, with each choice being equally likely to be picked. What is the probability they will correctly answer a question?

Answer:\
Let $A$ be the event that the student correctly answers a question.\
Let $B$ be the event that the student knows the answer to a question, so $\bar{B}$ is the event that the student does not know the answer to that question.\
$B$ and $\bar{B}$ are mutually disjoint events and $B \cup \bar{B}=\Omega$, so $\Pr(B)+\Pr(\bar{B})=\Pr(B \cup \bar{B})=\Pr(\Omega)=1$ and $\Pr(\bar{B})=1-\Pr(B)$.\
The student has degree of belief 0.8 that the student knows the answer, so $\Pr(B)=0.8$ and $\Pr(\bar{B})=1-\Pr(B)=1-0.8=0.2$.\
If the student does not know the answer, one of the six choices are chosen at random, and each choice is equally likely ot be picked.\
Therefore, the probability that the student chooses the correct answer given that the student does not know the answer is $\Pr(A|\bar{B})=\frac{1}{6}$.\
The student always answers correctly if the student knows the answer, so the probability that the student chooses the correct answer given that the student knows the answer is $\Pr(A|B)=1$.\
As a result, the probability that a question is answered correctly is $\Pr(A)=\Pr(A \cap B) + \Pr(A \cap \bar{B})=\Pr(A|B) \times \Pr(B)+\Pr(A|\bar{B}) \times \Pr(\bar{B})=1 \times 0.8 + \frac{1}{6} \times 0.2=\frac{5}{6}$.

6. A square of side 1 meter is drawn on a board, and a circle of radius 0.5m is inscribed within it. A dart is thrown at the board so that the dart is equally likely to land at any point in the square. What is the probability the dart lands somewhere within the circle?

Answer:\
For two events $A$ and $B$, $\Pr(A)=0.5$, $\Pr(B)=0.3$, $\Pr(A \cap B)=0.1$. Find $\Pr(A \cap B|A \cup B)$.
The area of the square is equal to $(1m) \times (1m)=1m^2$.\
The area of the circle is equal to $\pi \times (0.5m)^2=(0.25\pi)m^2$.\
The dart is equally likely to land at any point in the square on the board, so the probability that the dart lands within the circle = $\frac{number \ of \ atomic \ events \ that \ the \ dart \ lands \ within \ the \ circle}{number \ of \ atomic \ events \ that \ the \ dart \ lands \ in \ the \ square}=\frac{the \ area \ of \ the \ circle}{the \ area \ of \ the \ square}=\frac{(0.25\pi)m^2}{1m^2}=0.25\pi \approx 0.785$.

7. For two events $A$ and $B$, $\Pr(A)=0.5$, $\Pr(B)=0.3$, $\Pr(A \cap B)=0.1$. Find $\Pr(A \cap B|A \cup B)$.

Answer:\
$\Pr(A \cup B)=\Pr(A) + \Pr(B) - \Pr(A \cap B)=0.5 + 0.3 - 0.1 = 0.7$.\
$(A \cap B)$ is event containing all atomic events in both A and B, and $(A \cup B)$ is event containing all atomic events in A or B or both A and B. $(A \cap B) \cap (A \cup B)$ is event containing all atomic events in both $(A \cap B)$ and $(A \cup B)$.\
Therefore, 
$(A \cap B) \cap (A \cup B)=A \cap B.$\
$\Pr(A \cap B|A \cup B)=\frac{\Pr((A \cap B) \cap (A \cup B))}{\Pr(A \cup B)}=\frac{\Pr(A \cap B)}{\Pr(A \cup B)}=\frac{0.1}{0.7}=\frac{1}{7}.$

8. Suppose there are three events $A$, $B$, $C$ in a sample space so that $\Pr(A, B, C)>0$. Further we know that $A$ is independent of $B$. Show with an example for $A$, $B$, $C$ that it is not necessary that $A$ is independent of $B$, *given* $C$.

Answer:\
Let A be the event of getting odd number when tossing the first fair die with 6 sides. $\Pr(A)=\frac{3}{6}=0.5$\
Let B be the event of getting odd number when tossing the second fair die with 6 sides. $\Pr(B)=\frac{3}{6}=0.5$\
Let C be the event of getting a number that is smaller than 3 in that toss of the second fair die. $\Pr(C)=\frac{2}{6}=\frac{1}{3}$\
In this scenario, the first fair die and the second fair die are independent of each other; therefore, A is independent of B, and A is independent of C.\
Because A is independent of B and A is independent of C, $\Pr(A,B,C)=\Pr(A) \times \Pr(B,C)=0.5 \times \frac{1}{6}=\frac{1}{12} > 0$.\
$\Pr(A,B|C)=\frac{\Pr(A,B,C)}{\Pr(C)}=\frac{\frac{1}{12}}{0.5}=\frac{1}{6}$\
$\Pr(A|C)=\Pr(A)=0.5$ (because A is independent of C).\
$\Pr(B|C)=\frac{\Pr(B, C)}{\Pr(C)}=\frac{\frac{1}{6}}{\frac{1}{3}}=0.5$\
$\Pr(A|C) \times \Pr(B|C)=0.5 \times 0.5=0.25$ while $\Pr(A,B|C)=\frac{1}{6}$, so $(\Pr(A|C) \times \Pr(B|C))$ and $\Pr(A,B|C)$ are different and A is not necessarily independent of B given C.

9. You witness a night-time hit-and-run accident involving a taxi in Cleveland. All taxis in Cleveland are either red or blue. You state under oath that the taxi was red. Testing shows that, at night, discrimination between red and blue is 75% reliable. 60% of the taxis in Cleveland are blue. What is the most likely color of the taxi you saw?

Answer:  
I will calculate the probability of the car's color is actual red if I saw the car was red.
$
P(\text{the car's color is actual red if I saw the car was red}) $\ 
$= \frac{P(\text{testimony of red being correct based on reliability}).P(\text{any car being red})}
{P(\text{testimony of red being correct based on reliability}).P(\text{any car being red})+P(\text{testimony of red being wrong based on reliability}).P(\text{any car being blue})}$\
$= \frac{0.75 \times 0.4}{0.75 \times 0.4  \; + 0.25 \times 0.6} $\
$= \frac{0.75 \times 0.4}{0.75 \times 0.4  \; + 0.25 \times 0.6} = 0.67 $\
So the most likely color of the taxi is red, with a probability of 0.67. 
