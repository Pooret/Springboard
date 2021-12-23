# Relax Take Home Challenge
_A brief writeup_

## My approach to the problem
 The first obstacle that I addressed is creating the target variable that I will eventually use to make predictions (which I hope to do soon). To do this I wrote a function `adopted_user()` which takes in a user id and returns whether the user was considered adopted. 


        def adopted_user(user_id):
        
        """
        pseudocode:
          accepts user_id as an argument of type int. 
          returns true for 
            if in the span of the user's history
            if visits <= 3 for a period in the weekly frequency,
              if visits > 2 for all the days of that week
            If nothing found return False
        
            """

\n
I Then 
