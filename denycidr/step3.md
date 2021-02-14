We have to apply the ConstraintTemplate and the Constraint.

## ConstraintTemplate
The ConstraintTemplate has to be applied first.
First, we have to open the file and uncomment the rego policy lines that have been commented out after going through the policy. 

We can do this by removing the "**#**" before the start of each line.

For example, 

`#input.review.object.kind == "Pod"` becomes `input.review.object.kind == "Pod"`

## What the policy does
- It checks if the kind is Network Policy.
- Assign a variable 'cidr_or_ip' which will hold the value of IP CIDR range in the policy file.
- Another variable 'cidr' which holds the value of allowed IP CIDR ranges.
- We use a REGO built-in function, 'net.cidr_contains' to check if the provided IP is present
in the IP CIDR ranges that are allowed.

We will now apply the ConstraintTemplate.

`kubectl apply -f template.yaml`{{execute}}

## Constraint
Lets look at the constraint.yaml before applying.
- In the parameters array, we provide the allowed IP CIDR range.

`kubectl apply -f constraint.yaml`{{execute}}

**NOTE:** If "no matches for kind" error comes when applying the Constraint file, try the following fixes:
- Make sure all the rego policy lines have been uncommented. 
- Apply the template.yaml and the constraint.yaml again.
- If the error still persists, try applying the constraint.yaml again after a couple of minutes.
