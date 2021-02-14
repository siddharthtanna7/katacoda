We'll check if the policy is working as intended.

## violation.yaml
Take a look at the deployment-violation.yaml file before applying.

`kubectl apply -f deployment-violation.yaml`{{execute}}

This will get denied as the port is not in the allowed list of ports.

## non-violation.yaml
Take a look at the deployment-non-violation.yaml before applying.

`kubectl apply -f deployment-non-violation.yaml`{{execute}}

This will not get denied as the port matches the list of allowed ports.

