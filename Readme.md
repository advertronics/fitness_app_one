FITNESS TRACKING APP
INTRO:
The main purpopse of this app is to provide users with a tool they can evaluate their
current fitness status, get exercises and diet recommendations to achieve 
ideal fitness and be able to track their progress
METHODOLOGY:
The app will use Body Mass Index(BMI) as a fitness indicator.
BMI takes in the HEIGHT and WEIGHT of an individual and calculates health status as foolows:

          B.M.I = WEIGH(In KGS) / Square of (HEIGHT in METRES) 

An ideal B.M.I should between 18.5 and 24.9
Depending on the value, BMI gives three main health status (for simplicity purpose we choose 3 status)

Fitness Status 1: if B.M.I is BELOW 18.5 the individual is UNDERWEIGHT
Fitness Status 2: if B.M.I is between 18.5 and 24.9 the individual is FITNESS
Fitness Status 3: if B.M.I is ABOVE 24.9 the individual is OVERWEIGHT

IMPLEMENTATION:
The app will provide a registration dashboard and a first time user will be prompted
to put in username, email(will be the unique identifiers) and a password.
Then they will be directed to a login page where they can either login with username or email.
They will get a dashboard that will ask for their current HEIGHT and WEIGHT.
Based on this, the app will respond with the B.M.I value and indicate the health status.
If B.M.I indicates that the individual is UNDERWEIGHT, the app will give advise 
that the individual will need to gain how many kgs/lbs to achieve an ideal B.M.I
and consequently if according to the calculated B.M.I, the individual is OVERWEIGHT, the
app will advise how many Kgs/lbs the person needs to LOSE to achieve ideal B.M.I
In all cases, the app will give an workout and diet plan to be followe to achieve the goals
Everyweek, the individual will be logging in and feed in his/her weight and the app will draw a graph 
of progress and give indication on likelihood to achieve the goal...Awesome???

JAVASCRIPT OBJECT;
The app will create an object of the initial user details with username, email and password as properties.
Upon loggin in and providing height and weight, these will be UPDATED as additional properties in the user
object. A collection of all users will stored in an ARRAY of objects and stored in a backend database or localStorage(for testing purposes)
The user object will have method prototypes that will be called for the logged in user instance to calculate the B.M.I
and give the fitness status.

PSEUDOCODE
1. We will define a USER object using constructor that will be instantiated when the user registers.
2. The new USER will be added immediately to the database of users 
3. When the user logs in, there will be a dashboard that will collect the HEIGHT and WEIGHT, wraps them in another
object that we will call USER_DETAILS.
4. USER_DETAILS will update the USER object by creating two additional properties weight and height
5. We will create a USER prototype method(function), wqe shall call it CALCULATE_BMI that will take in the weight and height
of the USER instance and calclulate the B.M.I and returns either of these resposes once the user clicks 'calculate B.M.I'
button
6. if (B.M.I is below 18.5)
      return an object {
          weightToGain: 18.5 * square(height in metres) - current weight
          message: You are UNDERWEIGHT. you need to gain ${weightToGain}
          diet: a pdf file to be fetched from backend corresponding to weight gain 
          exercise: a pdf file of exercises for individuals to gain weight
      }
    else if (B.M.I is above 4.9)
       return an object {
          weightToLose: current weight - 24.9 * square(height in metres) 
          message: You are OVERWEIGHT. you need to lose ${weightToLose}
          diet: a pdf file to be fetched from backend corresponding to weight gain 
          exercise: a pdf file of exercises for individuals to gain weight
       }
    else {
        return an object {
            message: You are fit. keep exercising to maintain your fitness status!
        } 
    }
7. The different properties of the 'returned' object will be presented to the user by creating DOM elements 
for the user to view