# Business Problem

This project provides a CRUD web service for clients.

## Use cases

This is an example of a sequence diagram created using mermaid editor:

### Get one client


GET /clients/{id}

```mermaid

sequenceDiagram
    User->>Handler: /GET Client(id)
    Handler->>Service: GetClientByID(id)
    Service->>Repository: GetClientByID(id)

    alt user doesn't exist
        Repository-->>Service: error
        Service-->>Handler: errorNotFound
        Handler-->>User: 404 Not found
    else
        Repository-->>Service: client
        Service-->>Handler: clientStruct
        Handler-->>User: 200 - clientJson
    end

```