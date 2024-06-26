---
title: XDR_ALERT_CARD_WITH_TARGETS_AND_OBSERVABLES_TO_WEBEX_ROOM
integrated products: Webex
---

# XDR_ALERT_CARD_WITH_TARGETS_AND_OBSERVABLES_TO_WEBEX_ROOM

The goal of this workflow is to make XDR able to send an alert into an Alert Bot Room.

The alert is actually a Webex Adaptative card which is an interactive formular. 

The bot logic is not managed by XDR but XDR send into it an alert message which allow Security Operators to be aware of a Security issue and make them able to take isolation and blocking actions.

This workflow expect as inputs a target list, an observable list and an alert description.

Target and observable list must be into the following format :

    target-1
    target-2
    ....
    ....
    target-n
    
One single object per line. 

That means that any parsing and formating operation must have been done before to pass inputs to the workflow

---

## Change Log

| Date | Notes |
|:-----|:------|
| December 7, 2023 | - Initial release |
| January 16, 2024 | - Adding Isolation and Enforcement Point Selection. Bug Correction |

---

## Requirements

This workflow requires that an alert Webex bot with a room to interact with, had been setup

Instructions for creating a Webex Bot for XDR Alert can be found [here](https://github.com/pcardotatgit/Create_a_Webex_bot_for_XDR_Alerts)

## Input Variables

- target_list ( text variable with one observable per line )
- observable_list ( text variable with one observable per line )
- alert_description : A long text description of the alert

Default values are provided

---
## Global Variables

- XDR_ALERT_BOT_ROOM_ID : string : The Alert Bot Room ID 
- XDR_ALERT_BOT_TOKEN : secure_string :  The Alert Bot Room TOKEN
---
## Output Variables

No output variables

---

## Workflow Steps
1. The workflow reads the **target_list, observable_list and alert_description**
2. It creates the Webex Adaptative Card JSON payload ( the alert card )
3. It sends the alert cards JSON payload as attachment to the Alert Bot Room
---

## Installation and Configuration

* Import the **XDR_ALERT_CARD_WITH_TARGETS_AND_OBSERVABLES_TO_WEBEX_ROOM.json** workflow into your XDR tenant
* Assign correct values to the XDR_ALERT_BOT_ROOM_ID and XDR_ALERT_BOT_TOKEN
* You can run the workflow

---

## Targets


| Target Name | Type | Details | Account Keys | Notes |
|:------------|:-----|:--------|:-------------|:------|
| Webex XDR_ALERT_BOT_ROOM_ID | HTTP Endpoint | Managed by atomic subworkflow | | declared as a global variable |

---

## Account Keys

| Account Key Name | Type | Details | Notes |
|:-----------------|:-----|:--------|:------|
| XDR_ALERT_BOT_TOKEN | TOKEN | | declared as a global variable |

## Integrated Products

* Webex

# Where to go Next

Go to the following Section :

The [Send_XDR_Alert_to_every_Security_Operators](https://github.com/pcardotatgit/XDR_Workflows_and_Stuffs/tree/master/500-SecureX_Workflow_examples/Workflows/XDR_Send_XDR_Alert_to_every_Security_Operators_PROD) send exactly the same Alert but the destination differ.  Instead of sending the alert to a Webex alert Room, the alert is sent to a list of Security Operators that are in conversation with the XDR Alert Bot. 

And then go the all in one Use case which show a complete example of this alerting capability with demo. 

[Webex for XDR demo part 7 - the final demo](https://github.com/pcardotatgit/webex_for_xdr_part-7_The_final_demo)

Go back to the previous section 

[webex_for_xdr_part-5_websocket](https://github.com/pcardotatgit/webex_for_xdr_part-5_websocket)


## If I don't go to the final demo... What can I learn more ?

Connect AI to the Webex Bot !?   And talk with my Bot  ? Yeah !!

[ Let's go to this ](https://github.com/pcardotatgit/chatGPT_Webex_BOT)