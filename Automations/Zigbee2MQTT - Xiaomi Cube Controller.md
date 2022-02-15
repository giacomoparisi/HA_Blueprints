This Blueprint uses th Z2M (Zigbee2MQTT) imported Action sensor to sort out the multitude 
  of commands from the Xiaomi Magic Cube Remote.  The split out of functions gives you 
  the ability to assign local scripts or functions to do the things you want the remote to do.  
  Functions that are left empty will simply do nothing.  


## :arrow_down: Get Started

Updates will be published on my [GIT repository ](https://github.com/SirGoodenough/HA_Blueprints) with the rest of my Home Assistant Blueprint collection.

### Option 1: My Home Assistant

Click the badge to import this Blueprint (needs Home Assistant Core 2021.7 or higher for Trigger_ID to work)

[![Open your Home Assistant instance and show the blueprint import dialog with a specific blueprint pre-filled.](https://my.home-assistant.io/badges/blueprint_import.svg)](https://my.home-assistant.io/redirect/blueprint_import/?blueprint_url=https%3A%2F%2Fgithub.com%2FSirGoodenough%2FHA_Blueprints%2Fblob%2Fmaster%2FAutomations%2FZigbee2MQTT%2520-%2520Xiaomi%2520Cube%2520Controller.yaml)

### Option 2: Direct Link

Copy this link if you want to import the blueprint in your installation.
```https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT%20-%20Xiaomi%20Cube%20Controller.yaml```

https://github.com/SirGoodenough/HA_Blueprints/blob/master/Automations/Zigbee2MQTT%20-%20Xiaomi%20Cube%20Controller.yaml

## :page_facing_up: Description

This Blueprint uses a Zigbee2MQTT built sensor to sort out the multitude 
  of commands from the Xiaomi Magic Cube Remote.  The split out of functions gives you 
  the ability to assign local scripts or functions to do the things you want the remote to do.  
  Functions that are left empty will simply do nothing.  

  Within this code there is an event handler that will 'latch' the last command that the
  blueprint finds and sends that to the event buss.  From there a simple Template sensor 
  can grab it and show you the last action sent.  Thie will help  when setting up new
  functions and to troubleshoot strange behaviours.
  Here is a sample Template sensor to capture this event:
  ```yaml
  template:
    - trigger:
      - platform: event
        event_type: cube_last_action
    sensor:
    - name: "Cube Last Action"
      unique_id: Any-unique-string-here-MUST-be-unique
      state: '{{ trigger.event.data.event }} - {{ trigger.event.data.side }}'
  ```

Event Sensor in Action:
https://youtu.be/thaalK8pKtw

  If you wish to 'store' these events you can add this sensor to recorder and it will 
  save them for you.

  This was 'forked' from 'https://community.home-assistant.io/t/z2m-xiaomi-cube-controller/263006' 
  V1.2 project authored by luckypoppy and the friends he pulled together to create the base.  
  I sincerely thank Him (Them) for their work.  I felt there needed to be more documentation 
  for rookie users to properly set this up.  I had quite a few questions and when I saw a few questions 
  in that chat from people struggling, I wanted to help    
  I also had a better idea for troubleshooting info that didn't involve the log writes.


First, let’s go over Blueprints and what they are.  Blueprints are a way to share automations and is built into Home Assistant.  Simple as that.  You can import my template code and a copy of it will reside in your configuration.  Once there, you can can edit it (if you need changes only) or you can call up that Blueprint to build an automation.  It will collect the information needed based on your entities and your personal adjustments, and provide a working automation.  You will have to have or add the required hardware and entities that the Blueprint needs to function.

### How the Blueprint works:

To import this Blueprint: 
> • Open Home Assistant with administrator privileges and on a Lovelace screen, click anywhere in the main entity area and type the letter ‘c’.  A selection box should pop up.  Type blue and select the button to navigate to blueprints.  You can also find blueprints by selecting configuration from the left menu and then blueprints from the center menu.
> • Once there, click on the ‘Import Blueprint’ button in the lower right side of the main screen.
> • In the ‘URL of the blueprint’ line type or paste in the URL of my Blueprint. I have the blueprint stored on my Public GitHub:
>  ◦   https://github.com/SirGoodenough/HA_Blueprints

To make the Blueprint work you will need a functional Magic Cube integrated to Home Assistant thri Zigbee2MQTT and find the sensor that Z2M imported which is named like this>  
      sensor.XXYour_HameXX_action  
The other 4 sensors can be disabled, they will not be used.

Once you have the entities created or decided upon you can build the Automation.  To build the automation:  
> 1. Click on 'Create Automation
> 2. Add a Description so you can tell what this one is for
> 3. Use the Drop-downs to select the Entities for the listed purposes

## Changelog

* **2022-02-15**: Forked from https://community.home-assistant.io/t/z2m-xiaomi-cube-controller/263006 Version 1.2

# All My Blueprints

[Link to ALL my Blueprints](https://github.com/SirGoodenough/HA_Blueprints/blob/master/README.md)

Here is a list of each of my blueprints, a quick description and jump links to the Blueprints Exchange post...

## Scripts:
#### Broadlink on Script Blueprint

https://community.home-assistant.io/t/script-blueprint-to-turn-my-tv-on-and-put-it-into-the-correct-mode-for-the-input-device-i-want/338755

#### Tasmota EZ Button Blueprint

This Script Blueprint generates 3 Buttons to help you manage your Tasmota installed base.  Restart All, Update a few, and Update all.

https://community.home-assistant.io/t/script-blueprint-that-generates-3-ez-buttons-to-manage-your-tasmota-cluster/376934

#### Play Media File Script Blueprint Blueprint

This is a SCRIPT Blueprint. This provides a way to play canned media files with the big long list of YAML entries but keep the main script or automation clean. 

https://community.home-assistant.io/t/script-blueprint-to-play-media-player-files-not-an-automation-blueprint/371988

#### TTS Cloud Message Blueprint

This Script Blueprint plays a Nabu-Casa tts-cloud-say message in Home Assistant leaving the mess out of the main code.

https://community.home-assistant.io/t/script-blueprint-to-play-nabu-casa-tts-cloud-say-messages-not-an-automation-blueprint/377368

#### TTS Translate Say Message Blueprint

This Script Blueprint plays a Google Translate say message in Home Assistant leaving the mess out of the main code.

https://community.home-assistant.io/t/script-blueprint-for-google-translate-say-not-an-automation-blueprint/333199

## Automations:
#### Auto Fan Control Blueprint

This Blueprint is for controlling a 3 speed fan based on a temperature sensor.  Intended for Ifan03/Ifan04 but useful other places.

https://community.home-assistant.io/t/auto-fan-temperature-control-for-3-speed-fan-ifanxx-tasmota/326419

#### Door Open TTS Cloud-Say Message Blueprint

This Blueprint is a TTS.cloud-say version of another Door Announcer I found in the HA Blueprint Exchange.

https://community.home-assistant.io/t/door-open-tts-cloud-say-announcer-nabu-casa-required/316046

#### Keypad Lock or puzzle Box Tool Blueprint

This Blueprint accepts 5 actions & when done in the right order, flips an input_boolean.

https://community.home-assistant.io/t/keypad-cipher-code-for-5-button-presses-before-you-turn-on-an-input-boolean/322385


## Contact Links or see my other work:

What are we Fixing Today Homepage / Website: https://www.WhatAreWeFixing.Today/

Channel Link URL: (WhatAreWeFixingToday) https://bit.ly/WhatAreWeFixingTodaysYT

What are we Fixing Today Facebook page (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodaybFB

What are we Fixing Today Twitter Account (Sir GoodEnough): https://bit.ly/WhatAreWeFixingTodayTW

Discord Guild: (Sir_Goodenough#9683) https://discord.gg/Uhmhu3B

## If you want to support me:

Buy me Coffee: https://www.buymeacoffee.com/SirGoodenough

PayPal one-off donation link: https://www.paypal.me/SirGoodenough

Cash App $CASHTAG: https://cash.me/$SirGoodenough

Venmo cash link: https://venmo.com/SirGoodenough

#WhatAreWeFixingToday

#SirGoodEnough