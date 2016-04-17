---
layout: bt_wiki
title: Outputs
category: Blueprints
draft: false
weight: 600

---

## Outputs Declaration

The `outputs` section is a hash where each item in the hash represents an output.

hugo
outputs:
  output1:
    ...
  output2:
    ...
hugo


### Output Definition

Keyname     | Required | Type        | Description
----------- | -------- | ----        | -----------
description | no       | description | An optional description for the output.
value       | yes      | \<any\>     | The output value. Can be anything from a simple value (e.g. port) to a complex value (e.g. hash with values). Output values can contain hardcoded values, [inputs](hugo).

<br>

Example:

hugo
tosca_definitions_version: cloudify_dsl_1_2

imports:
  - http://www.getcloudify.org/spec/cloudify/3.3/types.yaml

node_templates:
  webserver_vm:
    type: cloudify.nodes.Compute
  webserver:
    type: cloudify.nodes.WebServer
    properties:
        port: 8080

output:
    webapp_endpoint:
        description: ip and port of the web application
        value:
            ip: { get_attribute: [webserver_vm, ip] }
            port: { get_property: [webserver, port] }
hugo

## Reading Outputs
You can view the outputs either by using the [cfy](cli-cfy-reference.html) CLI
hugo
cfy deployments outputs -d DEPLOYMENT_ID
hugo
or by making a REST call
hugo
curl -XGET http://MANAGER_IP/deployments/<DEPLOYMENT_ID>/outputs
hugo
