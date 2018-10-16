# mobile-developer-console-apb

This APB sets up the [Mobile Developer Console](https://github.com/aerogear/mobile-developer-console) for OpenShift.

## Local Development

### Requirements

- OpenShift Origin [development environment](https://github.com/ansibleplaybookbundle/ansible-playbook-bundle/blob/master/docs/getting_started.md#development-environment) for APB development.
- Install [apb tool](https://github.com/ansibleplaybookbundle/ansible-playbook-bundle/blob/master/docs/apb_cli.md)

### Process

Edit Makefile to point to your docker hub account

run `apb build; apb push`

## Testing

If you want to test the changes made to this repo, you can do it by simply running `apb test`
The test does the following:
1. Builds the APB 
1. Creates the project in currently targeted OpenShift instance
1. Runs the `provision` role
1. Runs the `test-provision` role which checks that
    * MDC route is accessible
    * we're getting successful response from OpenShift auth proxy server
1. Runs `deprovision` role
1. Runs `deprovision-test` role which checks that all objects (routes, pods, services etc) were deprovisioned (removed from namespace) successfully

If the test ends successfully, you should see the message `Pod phase Succeeded without returning test results` in your console output.

For more information about testing of APBs, check [ansible-playbook-bundle documentation](https://github.com/ansibleplaybookbundle/ansible-playbook-bundle/blob/master/docs/getting_started.md#test)
