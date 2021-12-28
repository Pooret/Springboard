# Relax Take Home Challenge
_A brief writeup_

For this take home challenge, I cleaned and preprocessed the data, created target variable "is_adopted" for users that have signed in at least three distint times over a period of 7-days, feature engineering to create flags for suspicious email names, domain names, frequent spammers, inactive users, and affiliations with known spam organizations. 

I thoroulgy enjoyed this take home challenge. I would suggest while looking at the code to listen to the soundtrack provided at the top, which is what I listed to while working on this (theme relax).


## My approach to the problem
 The first obstacle that I addressed is creating the target variable that I will eventually use to make predictions (which I hope to do soon). To do this I wrote a function `adopted_user()` which takes in a user id and returns whether the user was considered adopted.
 
 I then created the target feature `is_adopted` for the users DataFrame by passing the index of users (the user_id) to the function `adopted_user()` via the list comprehension
shown below. See code snippit.

   __Code Snippit__:     
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
            
            # Generate target variable "is_adopted" (needs a better name, works for now)
            `users['is_adopted'] = [adopted_user(user) for user in users.index]`
## Feature Engineering

I generated flags based off whether or not the email patterns were part of a recognizable domain *e.g. hotmail* and that some part of the name was in the username portion of the email *i.e. if either part of `["name_0",  ... "name_n" ]` as a list of the full name is part of the username*. Whether or not they were inactive. And if the are affiliated with any organizations that have been known to spam (see below).

      Most frequent invites by user_id
      0        4439
      2527       11
      10481      10
      10741      10
      1525       10
               ...
      Name: invited_by_user_id
      
 
               
## Cleaned and Encoded Table

The table below is the result of the data wrangling for the project. I did not have time, but I wanted to try encoding to an ordinal encoding for flags, org_id, and the type of invite, as it would do better than the one hot encoding with including the org_id column as it's cardinality is too high to one hot encode it.

|   object_id |   opted_in_to_mailing_list |   enabled_for_marketing_drip |   org_id |   account_age |   last_seen_active |   flags_username |   flags_domain |   flags_inactivity |   flags_org |   flags_spammers |   GUEST_INVITE |   ORG_INVITE |   PERSONAL_PROJECTS |   SIGNUP |   SIGNUP_GOOGLE_AUTH |
|------------:|---------------------------:|-----------------------------:|---------:|--------------:|-------------------:|-----------------:|---------------:|-------------------:|------------:|-----------------:|---------------:|-------------:|--------------------:|---------:|---------------------:|
|        4880 |                          0 |                            0 |       20 |           121 |                119 |                1 |              1 |                  0 |           0 |                0 |              0 |            1 |                   0 |        0 |                    0 |
|          83 |                          1 |                            0 |      172 |           496 |                495 |                0 |              0 |                  0 |           1 |                0 |              0 |            1 |                   0 |        0 |                    0 |
|        4051 |                          0 |                            1 |       47 |             8 |                  0 |                0 |              0 |                  0 |           1 |                0 |              0 |            1 |                   0 |        0 |                    0 |
|         656 |                          1 |                            1 |       42 |           497 |                497 |                0 |              0 |                  0 |           1 |                0 |              0 |            0 |                   0 |        0 |                    1 |
|        2935 |                          1 |                            1 |      394 |            61 |                 58 |                0 |              0 |                  0 |           1 |                0 |              0 |            0 |                   0 |        1 |                    0 |



## Modeling
I did several classifcation modeling studies, and example of the classification report of which is shown below for a random forest classifier validated on a holdout set.

                       precision    recall  f1-score   support

                    0       0.87      0.53      0.66      1689
                    1       0.11      0.42      0.17       231

             accuracy                           0.52      1920
            macro avg       0.49      0.48      0.42      1920
         weighted avg       0.78      0.52      0.60      1920
        
        
I would need to spend some more time modeling before I would feel comfortable talking about futher research that is needed. I need to do some feature selection and scaling studies, as well as test some universal approximator models to get a feel for how much improvement their needs to be in the model performance before I would know where further research should be done.

