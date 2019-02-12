# Assignment-16

# 1. A test is conducted which is consisting of 20 MCQs (multiple choices questions) with every MCQ having its four 
# options out of which only one is correct. Determine the probability that a person undertaking that test has 
# answered exactly 5 questions wrong.

import numpy as np
import matplotlib.pyplot as plt
from scipy.stats import binom
from scipy.special import factorial

#Assume that in an experiment , 'n' represent the trails attempted, 
#The count of successes that is to be attained in those ‘n’ trials is represented by 'k' 
#The failures is calculated as ‘n - k’.

n = 20
#n - k  = 5
Failures = 5
k = 15 

#Probability of success(Correct answer) = p_s
p_s = Failures / n
    
#Probability of failure (Wrong answer)=p_f 
p_f = 1 - p_s

#Using the formula for binomial distribution we get the probability value as

P = (factorial(n) /(factorial(k) * factorial(n - k))) * np.power(p_s,k) * np.power(p_f,Failures)

print("The probability of getting exactly 5 out of 20 answers incorrect is {:0.7f}".format(P))

# 2. A die marked A to E is rolled 50 times. Find the probability of getting a “D” exactly 5 times.

#Assume that in an experiment , 'n' represent the trails attempted, 
#The count of successes that is to be attained in those ‘n’ trials is represented by 'k' 
#The failures is calculated as ‘n - k’.
 
n = 50
k =5
Failures = n - k
#Probability of success (Getting a 'D')= p_s
p_s = 1/k

#Hence, the probability of failure (Not getting a 'D')= p_f 
p_f = 1 - p_s 

print("The probability of getting a 'D' in {} throws out of  {} number of trails conducted is {}".format(k,n,p_s))

# 3.Two balls are drawn at random in succession without replacement from an urn containing 4 red balls and 6 black balls.
# Find the probabilities of all the possible outcomes.

red_ball = 4
black_ball = 6
total_balls = red_ball + black_ball

#Possible outcomes= {Red_ball and Black_ball,Black_ball and Red_ball,Black_ball and Black_ball,Red_ball and Red_ball}

#So the chances of picking a red ball first is 4 out of 10 balls. So the probability is 4/10.
p_first_red_ball = red_ball / total_balls

#So the chances of picking a black ball second is 6 out of 9 balls. So the probability is 6/9.
p_second_black_ball  = black_ball / (total_balls - 1)

#So the chances of picking a black ball  first is  6 out of 10 balls. So the probability is 6/10.
p_first_black_ball = black_ball / total_balls

#So the chances of picking a red ball second is 4 out of 9 balls. So the probability is 4/9.
p_second_red_ball  = red_ball / (total_balls - 1)
#Probability that both the balls are red is computed here as:
#= Total number of ways to select 2 red balls from the 4 red balls / 
#    Total number of ways to select 2 black  balls from 10 total balls

P_2_r  = (factorial(red_ball) / (factorial(2) * factorial(red_ball - 2))) / (factorial(total_balls) 
                                                                             / factorial(2)* factorial(total_balls - 2))

#Probability that both the balls are black is computed here as:
#= Total number of ways to select 2 black balls from the 6 red balls / 
#    Total number of ways to select 2 black  balls from 10 total balls

P_2_b  = (factorial(black_ball) / (factorial(2) * factorial(black_ball -2))) / (factorial(total_balls) 
                                                                                / factorial(2)* factorial(total_balls - 2))
                                                                                
print("The probabilities of all possible outcomes of picking Red ball first,Black Ball second is ({:0.2f},{:0.2f})".format
      (p_first_red_ball,p_second_black_ball))
print("The probabilities of all possible outcomes of picking black ball first,red Ball second is ({:0.2f},{:0.2f})".format
      (p_first_black_ball,p_second_red_ball))
print("The probabilities of all possible outcomes of picking both the balls as black is {:0.10f}".format(P_2_b))
print("The probabilities of all possible outcomes of picking both the balls as red is {:0.10f}".format(P_2_r))
