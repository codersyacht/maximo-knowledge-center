# Integration - Post Message to External System

### Author: Mohamed Jawahar Hussain

## Introduction

Post message to an external JMS queue when a work order is created.

## Prerequisite

- JMS Server configured and running.
- Maximo configured to function as JMS client.

## Process Diagram

## Execution Steps

The endpoint is the external system to which message is to be posted.
Complete endpoint definition by following the instruction [here](/maximo/docs/integration/endpoints.md)

Configure the Publish channel that defines which object to publish. Ensure to provide the object structure as **MXWO**. Follow the instructions [here](/maximo/docs/integration/publish-channels.md)

Configure the External System binding the Endpoint and the Publish Channel following the instructions [here](/maximo/docs/integration/external-systems.md)
