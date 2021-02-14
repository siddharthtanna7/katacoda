We have to apply the ConstraintTemplate and the Constraint.

## ConstraintTemplate
The ConstraintTemplate has to be applied first.
First, we have to open the file and uncomment the rego policy lines that have been commented out after going through the policy. 

We can do this by removing the "**#**" before the start of each line.

For example, 

`#input.review.object.kind == "Pod"` becomes `input.review.object.kind == "Pod"`

## What the policy does
- A variable 'allowed' will store the list/ranges of allowede ports.
- A variable 'provided' will store the port/port ranges provided.
- If the provided value does not match the allowed one, it will be denied.

We will now apply the ConstraintTemplate.

`kubectl apply -f template.yaml`{{execute}}

## Constraint
Lets look at the constraint.yaml before applying.
- Constraints will have a parameter with the port that you want to allow.

`kubectl apply -f constraint.yaml`{{execute}}

**NOTE:** If "no matches for kind" error comes when applying the Constraint file, try the following fixes:
- Make sure all the rego policy lines have been uncommented. 
- Apply the template.yaml and the constraint.yaml again.
- If the error still persists, try applying the constraint.yaml again after a couple of minutes.
