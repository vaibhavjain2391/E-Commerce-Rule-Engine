E-Commerce-Rule-Engine
======================

Rule Engine implemented in Python. The project came second in Zivame Hacakathon-2014.The algorithm was designed and implemented in the 24 hour hacking session.

Given a set of rules for discount, we need to apply a specific rule on the shopping cart. A simple example is applying discount=10% on total purchase greater then 500usd and applying discount= 15% on total purchase more then 1000usd. The rules can become more complex as we keep on including factors like item category, method of payment, place, customer etc. apart from cart value. Refer to the problem statement pdf enclosed for a better idea. 

Basic work is to match shopping cart json content with every rule and find out if it qualifies. The rules can be traversed in their priority order to return the first matched rule. However, we may have to check a lot number of totally unrelated rules this way. Is it possible to prune out rules before-hand which are not applicable completely ? Another observation is rules will change very less frequently as compared to shopping cart API called in any popular e-commerce website. Can we do some offline work on rules data to save time online ? 

Idea : For every category, create an array which stores all the applicable rules. Whenever a shopping cart json comes, traverse these arrays to find the intersection i.e. rules applicable to all the categories inside shopping cart. Consult the priority list to output the highest priority rule.

Implementation Details :
parsingInput.py : JSON content of the shopping cart.
parsingRules.py : Rules content in JSON format.
fillRulesInfo.py : Create the category arrays. Two categories were handled : cart total, item category. This can be scaled with the requirement.
applyRules.py :This is the main file which calls every other file.Given the shopping cart input and rules, we need to output the best matching rule.
adminInfo.py : File maintained by admin to store rules priority, rule offers etc.

