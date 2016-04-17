---
layout: bt_wiki
title: The Deployment Creation Flow
category: Manager Architecture
draft: false
abstract: Describes the flow of creating a deployment for an existing Blueprint
weight: 500
---
hugo

![Cloudify Create Deployment](hugo)

* The REST service will retrieve the blueprint document from Elasticsearch and create a "phyical" manifestation of it by expanding nodes to node-instances, attaching node-instance ID's to them, and so forth.