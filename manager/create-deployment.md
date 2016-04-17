---
layout: bt_wiki
title: Creating a Deployment
category: Manager Intro
draft: false
weight: 500

terminology_link: reference-terminology.html
---

For Cloudify to be able to deploy your application it reads the uploaded blueprint YAML (the logical representation) and manifests a model we call a `deployment`. A deployment is a "Technical" drilled down representation of your application. For instance, if a blueprint describes a single server node that is defined to deploy multiple instances, the deployment will comprise the instances themselves provided with their unique identifiers.


## Creating a Deployment via the CLI

To create a deployment using Cloudify's CLI execute:

hugo
cfy deployments create -b <BLUEPRINT_NAME> -d <DEPLOYMENT_NAME> --inputs </path/to/your/inputs.yaml​>
hugo


## Creating a Deployment via the Web UI

To Create a new deployment, go to the blueprints screen, choose a blueprint and click on the button `Create Deployment`:<br/>
![Create deployment button](hugo)

A create deployment dialog will open.<br/>

Next, please fill out the deployment name and insert raw input parameters (optional), then click on the `create` button:<br/>
![Create deployment box](hugo)

After creating the deployment, you will be directed to the deployment's page to follow the initialization stage:<br/>
![Deployment initialize](hugo)

Once the initialization is complete, you will be able to start using the deployment and execute [workflows](hugo#workflow).<br/>
![Deployment ready to use](hugo)

# Create a Deployment

Picking up from Step 5, [Uploading a Blueprint](getting-started-upload-blueprint.html), we'll now create the deployment for our blueprint using the command line.

hugo
Creating a Deployment doesn't actually create any resources, it simply generates a "Physical" representation of your application from the "Logical" (Blueprint) representation and stores in the database. Technically, it is a virtual environement on the manager.
hugo

First create an inputs file (just like our Manager Blueprint's inputs dialog):


  hugo

  hugo

  hugo

  hugo
  inputs:
    image:
      description: >
        Image to be used when launching agent VM's
    flavor:
      description: >
        Flavor of the agent VM's
    agent_user:
      description: >
        User for connecting to agent VM's
  hugo


Let's make a copy of the inputs template already provided and edit it:

  hugo
  cd cloudify-nodecellar-example/inputs/openstack.yaml.template
  cp openstack.yaml.template inputs.yaml
  hugo
  The inputs.yaml file should look somewhat like this:
  hugo
  image: 8c096c29-a666-4b82-99c4-c77dc70cfb40
  flavor: 102
  agent_user: ubuntu
  hugo

  hugo

  hugo

  hugo
  inputs:
    location:
      description: >
        Location of the data center
        Default value is the location id of Hong kong 2
      default: 352494
    domain:
      description: The domain
      default: nodecellar.cloudify.org
    ram:
      description: >
        Item id of the ram
        Default value is the item id of 16 GB
      default: 1017
    cpu:
      description: >
        Item id of the cpu
        Default value is the item id of 4 x 2.0 GHz Cores
      default: 859
    disk:
      description: >
        Item id of the disk
        Default value is the item id of 25 GB (SAN)
      default: 1178
    os:
      description: >
        Item id of the operating system
        Default value is the item id of Ubuntu Linux 12.04
      default: 4174
  hugo

All inputs have default values so no input file is needed.

To specify differnet values for one or more inputs, create inputs.yaml file with the wanted inputs, for example:

  hugo
  echo -e "domain: 'my_domain.org'\nlocation: '168642'" > inputs.yaml
  hugo
  The inputs.yaml file will look like this:
  hugo
  domain: 'my_domain.org'
  location: '168642'
  hugo

  hugo

  hugo

  hugo
  inputs:
    image:
      description: >
        Image to be used when launching agent VM's
    flavor:
      description: >
        Flavor of the agent VM's
    agent_user:
      description: >
        User for connecting to agent VM's
  hugo

Let's make a copy of the inputs template already provided and edit it:

  hugo
  cd cloudify-nodecellar-example/inputs
  cp aws-ec2.yaml.template inputs.yaml
  hugo
  The inputs.yaml file should look somewhat like this:
  hugo
    image: ''
    size: ''
    agent_user: ''
  hugo

The image is again the AMI image ID. The size is the instance_type, and the agent user is the default user agent on the image type.

  hugo

  hugo

  hugo
  inputs:
    vcloud_username:
        type: string
    vcloud_password:
        type: string
    vcloud_url:
        type: string
    vcloud_service:
        type: string
    vcloud_vcd:
        type: string
    catalog:
      type: string
    template:
      type: string
    agent_user:
      type: string
      default: ubuntu
    management_network_name:
      type: string
    floating_ip_gateway:
      type: string
    nodecellar_public_ip:
      type: string
  hugo

Let's make a copy of the inputs template already provided and edit it:

  hugo
  cd cloudify-nodecellar-example/inputs
  cp vcloud.yaml.template inputs.yaml
  hugo
  The inputs.yaml file should look somewhat like this:
  hugo
  {
      "vcloud_username": "your_vcloud_username",
      "vcloud_password": "your_vcloud_password",
      "vcloud_url": "https://vchs.vmware.com",
      "vcloud_service": "service_name",
      "vcloud_vdc": "virtual_datacenter_name",
      "manager_server_name": "your_manager",
      "manager_server_catalog": "templates_catalog",
      "manager_server_template": "template",
      "edge_gateway": "gateway_name",
      "floating_ip_public_ip": "",
      "management_network_name": "management",
      "manager_private_key_path": "~/.ssh/vcloud_template.pem",
      "agent_private_key_path": "~/.ssh/vcloud_template.pem"
  }
  hugo

  hugo

  hugo

  hugo


Now that we have an inputs file, type the following command:

hugo

cfy deployments create -b nodecellar -d nodecellar --inputs inputs.yaml

hugo

We've now created a deployment named `nodecellar` based on a blueprint with the same name.

This deployment is not yet materialized, since we haven't issued an installation command.

If you click the "Deployments" icon in the left sidebar in the Web UI, you will see that all nodes are labeled with 0/1, which means they're pending creation.

![Nodecellar Deployment](hugo)


# What's Next

After creating a deployment, you're now ready to [execute it!](getting-started-execute-workflow.html).
