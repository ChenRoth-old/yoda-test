---
layout: bt_wiki
title: Workflow execution in the UI
category: Web Interface
draft: false
abstract: Workflow badges Reference
weight: 135

execute_workflow_link: getting-started-execute-workflow.html
---
hugo

When executing a `Workflow` for a `Deployment` (e.g. the `install` workflow), the topology nodes show badges that reflect the workflow execution state.<br/>
See more details on executing workflows [here](hugo#topology).<br/>

## Badges

* Install state - The workflow execution is in progress for this node
* Done state - The workflow execution was completed successfully for this node
* Alerts state - The workflow execution was partially completed for this node
* Failed state - The workflow execution failed for this node

![Deployment Topology Node Badges](hugo)

## Workflow states represented by badges
A deployment before any workflow was executed
![Deployment Topology](hugo)

A deployment with a workflow execution in progress
![Deployment Topology Execution In Progress](hugo)

A deployment with a workflow execution in progress, partially completed
![Deployment Topology Execution Partially Completed](hugo)

A deployment with a workflow execution completed successfully
![Deployment Topology Execution Completed Successfully](hugo)

A deployment with a workflow execution partially completed successfully with some alerts
![Deployment Topology Execution Completed Partially Alerts](hugo)

A deployment with a workflow execution that partially failed
![Deployment Topology Execution Completed Partially Errors](hugo)

A deployment with a workflow execution that failed
![Deployment Topology Execution Completed Errors](hugo)
