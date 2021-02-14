We'll check if the policy is working as intended.

## violation.yaml
Take a look at the deployment-violation.yaml file before applying.

`kubectl apply -f deployment-violation.yaml`{{execute}}

This will get denied as the IP is not in the CIDR range.

## non-violation.yaml
Take a look at the deployment-non-violation.yaml before applying.

`kubectl apply -f deployment-non-violation.yaml`{{execute}}

This will not get denied as the IP is in the CIDR range.

