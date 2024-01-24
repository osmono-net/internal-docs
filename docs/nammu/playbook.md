# Playbook Commands

'Playbook' is the term used to refer to sending powershell (or other langs?) over the wire, to be executed by a specific agent.

This is done via a 'Request-Reply' pattern, via the `nammu-playbook-command` channel.

The API server sends a `Request` on this channel, containing the AgentID, and the action to be performed. 
The agent will then determine if the request is for itself via the ID. 

Then, the agent will execute a certain script. An example `Request` is seen below:

```json
TODO
```

TODO
