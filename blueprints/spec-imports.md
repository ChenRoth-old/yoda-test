---
layout: bt_wiki
title: Imports
category: Blueprints
draft: false
weight: 200

types_yaml_link: http://www.getcloudify.org/spec/cloudify/3.3/types.yaml
dsl_node_types_link: dsl-spec-node-types.html
dsl_groups_link: dsl-spec-groups.html
dsl_inputs_link: dsl-spec-inputs.html
dsl_outputs_link: dsl-spec-outputs.html
dsl_node_templates_link: dsl-spec-node-templates.html
dsl_versioning_link: dsl-spec-versioning.html
---

# Declaration

hugo
imports:
  - ...
  - ...
hugo


# Example

hugo

imports:
  - hugo
  - my_yaml_files/openstack_types.yaml

node_templates:
  vm:
    type: cloudify.openstack.nodes.Server
  webserver:
    type: cloudify.nodes.WebServer
hugo

In the above example, we import the default types.yaml file provided by Cloudify which contains the `cloudify.nodes.WebServer` [node type](hugo) and a custom YAML we created for our custom OpenStack plugin containing the `cloudify.openstack.nodes.Server` node type.

A few important things to know about importing YAML files:

* Imported files can be either relative to the blueprint's root directory or be a URL (as seen above).
* You can use imports within imported files and nest as many imports as you like.
* An error will be raised if there are cyclic imports (i.e. a file is importing itself or importing a file which is importing the file that imported it, etc..)
* The following parts of the DSL cannot be imported and can only be defined in the main blueprint file:
    * [groups](hugo)
    * [inputs](hugo)
    * [node_templates](hugo)
    * [outputs](hugo)
* The `tosca_definitions_version` as stated [here](hugo) must match between imported files.
