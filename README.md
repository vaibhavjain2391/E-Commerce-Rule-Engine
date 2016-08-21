E-Commerce-Rule-Engine
======================

Summary of rule Engine implemented in Python. The project came second in 24 hour Zivame Hackathon-2014.

Given a set of rules with priorities for discount/surcharge, we need to find out which one is applicable on a given shopping cart optimally. A simple example is applying discount=10% on total purchase greater thsn 500 bucks and applying discount= 15% on total purchase more than 1000 bucks. The rules can become more complex as we keep on including factors like item category, method of payment, place, customer history etc. apart from cart value. Refer to the problem statement pdf enclosed for more details. 

Brute force method is to compare shopping cart json content with every rule and find out if it qualifies. The rules can be traversed in their priority order to return the first matched rule. However, we may have to check a lot number of totally unrelated rules this way. Is it possible to prune out rules before-hand which are not applicable at all ? Another observation is rules will change very less often as compared to shopping cart API hits in any popular e-commerce website. Can we do some offline work on rules data to save time online ? 

Idea : For every category, create an array which stores all the applicable rules. Whenever a shopping cart json comes, find out rules applicable for every individual category. Rules applicable to all the categories inside shopping cart will be the intersection. Consult the priority list to output the highest priority rule.

Implementation Details :

parsingInput.py : JSON content of the shopping cart.

parsingRules.py : Rules content in JSON format.

fillRulesInfo.py : Create the category arrays. Two categories were handled : cart total, item category. This can be scaled with the requirement.

applyRules.py :This is the main file which calls every other file.Given the shopping cart input and rules, we need to output the best matching rule.

adminInfo.py : File maintained by admin to store rules priority, rule offers etc.

