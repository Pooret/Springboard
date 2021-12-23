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

## Cleaned and Preprocessed Table

|   object_id |   opted_in_to_mailing_list |   enabled_for_marketing_drip |   org_id |   account_age |   last_seen_active |   flags_username |   flags_domain |   flags_inactivity |   flags_org |   flags_spammers |   GUEST_INVITE |   ORG_INVITE |   PERSONAL_PROJECTS |   SIGNUP |   SIGNUP_GOOGLE_AUTH |
|------------:|---------------------------:|-----------------------------:|---------:|--------------:|-------------------:|-----------------:|---------------:|-------------------:|------------:|-----------------:|---------------:|-------------:|--------------------:|---------:|---------------------:|
|        4880 |                          0 |                            0 |       20 |           121 |                119 |                1 |              1 |                  0 |           0 |                0 |              0 |            1 |                   0 |        0 |                    0 |
|          83 |                          1 |                            0 |      172 |           496 |                495 |                0 |              0 |                  0 |           1 |                0 |              0 |            1 |                   0 |        0 |                    0 |
|        4051 |                          0 |                            1 |       47 |             8 |                  0 |                0 |              0 |                  0 |           1 |                0 |              0 |            1 |                   0 |        0 |                    0 |
|         656 |                          1 |                            1 |       42 |           497 |                497 |                0 |              0 |                  0 |           1 |                0 |              0 |            0 |                   0 |        0 |                    1 |
|        2935 |                          1 |                            1 |      394 |            61 |                 58 |                0 |              0 |                  0 |           1 |                0 |              0 |            0 |                   0 |        1 |                    0 |
