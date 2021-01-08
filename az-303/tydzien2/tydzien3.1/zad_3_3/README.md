#TYDZIEN3.3 „Zbuduj najprostrz¹ w³aœn¹ rolê RBAC, która pozwala u¿ytkownikowi uruchomiæ maszynê, zatrzymaæ j¹ i zg³osiæ zg³oszenie do supportu przez Portal Azure”


{
  "Name": "Custom Virtual Machine Operator",
  "Id": "88c6bf36-92e2-4dde-a66c-4b3ecf08c53c",
  "IsCustom": true,
  "Description": "Can start, stop virtual machines and open a ticket to support.",
  "Actions": [
    "Microsoft.Compute/virtualMachines/start/action",
    "Microsoft.Compute/virtualMachines/restart/action",
    "Microsoft.Support/supportTickets/write"
  ],
  "NotActions": [],
  "DataActions": [],
  "NotDataActions": [],
  "AssignableScopes": [
    "/subscriptions/88c6bf36-92e2-4dde-a66c-4b3ecf08c53c",
  ]
}



