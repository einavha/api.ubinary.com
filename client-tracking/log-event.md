## Track client event

#### Request

GET http://api.ubinary.com/bm/client/event/DEVICE_ID/SESSION_ID/VERSION/WORKFLOW/ACTION/LABEL

where 
  - DEVICE_ID: string - random cookie based device id
  - SESSION_ID: string - random session id per html page lifetime
  - VERSION: integer - workflow version number
  - WORKFLOW: string - workflow name
  - ACTION: string - action name whithin a workflow
  - LABEL: string - optional status of an action or ...

##### A valid request example

http://api.ubinary.com/bm/client/event/424324/34-32-54/1/registration/LoadLibs/done