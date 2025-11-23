# Websocket API Protocol

This document describes the protocol for comunication between VISTA and SPINE components of ROUTE.

## Types on websocket events

### Action

Actions are sent by the VISTA.

```json
{
  "action": "<domain>.<action>",
  "params": {
    "param_1": "param_1_value",
    "param_2": "param_2_value",
    ...
  }
}
```

### Signal

Signals are sent by the SPINE.

```json
{
  "signal": "<domain>.<signal>",
  "data": {
    "param_1": string,
    "param_2": number,
    ...
  }
}
```

## Allowed Actions

### Starting Simulation

```json
# On the action sent by a client:
{
  "action": "simulation.start",
  "params": {
    "tick_rate": integer
  }
}

# Server responses with:
{
  "signal": "simulation.started",
  "data": {
    "tick_rate": integer
  }
}
```

### Stopping Simulation

```json
# On the action sent by a client:
{
  "action": "simulation.stop",
  "data": {}
}

# Server responses with:
{
  "signal": "simulation.stopped",
  "data": {}
}
```

### Pausing Simulation

```json
# On the action sent by a client:
{
  "action": "simulation.pause",
  "data": {}
}

# Server responses with:
{
  "signal": "simulation.paused",
  "data": {}
}
```

### Resuming Simulation

```json
# On the action sent by a client:
{
  "action": "simulation.resume",
  "params": {}
}

# Server responses with:
{
  "signal": "simulation.resumed",
  "data": {}
}
```

### Update Simulation

```json
# On the action sent by a client:
{
  "action": "simulation.update",
  "params": {
    "tick_rate": integer,
    "speed": float
  }
}

# Server responses with:
{
  "signal": "simulation.updated",
  "data": {
    "tick_rate": integer,
    "speed": float
  }
}
```

### Create Map

```json
# On the action sent by a client:
{
  "action": "map.create",
  "params": {
    "size": number,
    ...
  }
}

# Server responses with:
{
  "signal": "map.created",
  "data": {
    "size": number,
    ...
  }
}
```

```json
# On the action sent by a client:
{
  "action": "map.export",
  "params": {
    "map_name": string
  }
}

# Server responses with:
{
  "signal": "map.exported",
  "data": {
    "filename": string,
    "base64_file": string
  }
}
```

### Importing Map

```json
# On the action sent by a client:
{
  "action": "map.import",
  "params": {
    "base64_file": string,
  }
}

# Server responses with:
{
  "signal": "map.imported",
  "data": {}
}
```

### Adding an Agent

```json
# On the action sent by a client:
{
  "action": "agent.create",
  "params": {
    "agent_id": string,
    "agent_kind": string,
    ...
  }
}

# Server responses with:
{
  "signal": "agent.created",
  "data": {
    "agent_id": string,
    "agent_kind": string,
    ...
  }
}
```

### Updating an Agent

```json
# On the action sent by a client:
{
  "action": "agent.update",
  "params": {
    "agent_id": string,
    ...
  }
}

# Server responses with:
{
  "signal": "agent.updated",
  "data": {
    "agent_id": string,
    ...
  }
}
```

### Deleting an Agent

```json
# On the action sent by a client:
{
  "action": "agent.delete",
  "params": {
    "agent_id": string
  }
}

# Server responses with:
{
  "signal": "agent.deleted",
  "data": {
    "agent_id": string
  }
}
```

### Geting Agent State

```json
# On the action sent by a client:
{
  "action": "agent.describe",
  "params": {
    "agent_id": string
  }
}

# Server responses with:
{
  "signal": "agent.described",
  "data": {
    "agent_id": string,
    "agent_kind": string,
    ...
  }
}
```

### List all agents

```json
# On the action sent by a client:
{
  "action": "agent.list",
  "params": {
    "agent_kind": string
  }
}

# Server responses with:
{
  "signal": "agent.listed",
  "data": {
    "total": integer,
    "agents": [
      {
        "agent_id": string,
        ...
      },
      {
        "agent_id": string,
        ...
      },
      ...
    ],
  }
}
```

## Allowed Signals

### Event

Generic event happening in the legistics network

```json
{
  "signal": "event.created",
  "data": {
    "event_name": string,
    ...
  }
}
```

### Change to the building's state

```json
{
  "signal": "building.updated",
  "data": {
    "building_id": string,
    ...
  }
}
```

### Change to the agent's state

```json
{
  "signal": "agent.updated",
  "data": {
    "agent_id": string,
    ...
  }
}
```

### Error

Generic error returned by the SPINE when anything goes wrong

```json
{
  "signal": "error",
  "data": {
    "code": string,
    "message": string
  }
}
```
