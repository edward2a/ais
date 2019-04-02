# Configuration Source

There are various places where a centralised configuration source could not only be beneficial but also improve efficiency in the way that configurations are delivered to these locations and the processes involved into the creation, maintenance and deprecation of such configuration assets.

A setup like AIS would allow the information required at different stages to be sourced an controlled from a single place (or multiple places with a single end-user interface).

## Virtual Machine Provisioning
On the creation and/or configuration of virtual machine images, multiple parameters are used which are often hard-coded either in the execution process (say in the packer file) or in some form of (still static) config file used in this process.
This information could be obtained on run-time (or pre run-time) from a central information store (AIS).
For example, these are candidate items (assets) that could be fetched dynamically:
  - name of the base machine image
  - location of the artifact store
  - version of chef client
  - version of java 8
  - version of the applicaiton to be deployed for the target environment


## Infrastructure as Code
When deploying infrastructure as code, a similar pattern is observed as in the virtual machine provisioning case, however the settings are different.
For example, lets assume there is a baseline configuration for an application that indicates a safe minimum of instances of 2, the required for dev environment. For production this would be, for example, 4.

When the IaC tool deploys it would use this values stored in somewhere. Often this is accompanied to the IaC files (\*.tf in case of terraform).
For any configuration changes, this would mean an actual 'code change', BUT, there is no actual code changes, rather configuration.

One could argue that the separation of code and configuration could be achieved by having a separate repository for configuration, which is doable and it works. However, the objective of AIS is to provide a central model for asset storage, and configuration can also be considered an asset.

So in the case of infrastructure as code, a pre-processor tool (just a script fetching the values) or IaC tool integration itself, could simply fetch the configuration from AIS by performing a HTTP call like to an endpoint like 'https://ais.example.com/project/<project-name>/config/<env-name>/current' and AIS would return a config file used for the infrastructure deployment.


## Software Configuration
