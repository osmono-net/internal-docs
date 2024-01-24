# Remote Configuration

Configuration in nammu is done in one of two stages:


## Pre-Intial Stage

When we create an installer for an agent, we embed a customer ID into the installer via TODO method. For now, we are just gonna pretend theres a nice customer_id.txt file on disc in X path. This is obviously insecure

## Initial Stage

An agent, when first installed onto a machine sends a registration `POST` request to the Osmono API server.
This request includes important information about the machine. The agent is then registered as active, and the agent is assigned an ID. It saves this ID in a file on disk.

The agent will then send a `GET` to `/agent/{id}/config`. The API server will create a default config for
the agent, depending on the information received in the registration request.

The agent uses this config to determine its actions going forward. The agent is now in 'service' mode, where it will continually run, and receive instructions from the server.


## Service Stage

If the API server determines that the agent needs to change its config for some reason, this could be automated, or because of a change by the owning Organization. The agent receives this update via the `nammu-{orgid}-config` channel.

If the agent notices an important change in the state of the machine it is running in, it will send this information onto the server. If the server decides this information should result in a config change, it will send that as per the above paragraph.
