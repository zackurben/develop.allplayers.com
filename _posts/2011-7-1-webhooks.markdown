---
layout: default
title: Webhooks
---
# AllPlayers Webhooks

Every Group on AllPlayers has the ability to communicate with an external web server via Webhooks. When a Webhook is triggered the related data, encoded in JSON or form-urlencoded, is sent to your specified external URL. These Webhooks can be used to update your external application using our internal data. You can view the contents and types of available Webhooks below.

### Enabling Webhooks
1. Open the Group page on AllPlayers.com, and go to the Features page:
![](../images/webhooks1.png)

2. Enable the Webhooks on the Group, and then go to the Settings page:
![](../images/webhooks2.png)

3. Enter your desired URL, activate the Webhook, and click on Save:
![](../images/webhooks3.png)

### Types of Webhooks

There are currently six Webhooks. These include:

Webhook Name | Description
:------------ | :------------
user_creates_group | Triggered when a sub group is created.
user_updates_group | Triggered when a sub group has its settings edited.
user_deletes_group | Triggered when an admin deletes the Group.
user_adds_role | Triggered when a user is assigned a role within a sub group (eg. A user registers for a position in a group.)
user_removes_role | Triggered when a user has an attached role removed from its account (eg. A admin removes a role from a member within the group).
user_adds_submission |Triggered when a user registers for a role and the role has a webform. When the webform is filled out and submitted along with the users registration, the user_adds_submission webhook gets called.

### Webhook Templates

The following are examples of our Webhooks, using the JSON response option.

```
user_creates_group
```
```json
{
    "uuid": "00000000-0000-0000-0000-000000000000",
    "group": {
        "uuid": "00000000-0000-0000-0000-000000000000",
        "name": "group",
        "description": "group",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "i"
        ],
        "url": "https://www.allplayers.com/g/group",
        "logo": "https://www.allplayers.com/",
        "group_above": "00000000-0000-0000-0000-000000000000"
    },
    "webhook_type": "user_creates_group",
    "submissions": []
}
```

```
user_updates_group
```
```json
{
    "uuid": "00000000-0000-0000-0000-000000000000",
    "group": {
        "uuid": "00000000-0000-0000-0000-000000000000",
        "name": "group",
        "description": "group",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "00000000-0000-0000-0000-000000000000"
        ],
        "url": "https://www.allplayers.com/g/group",
        "logo": "https://www.allplayers.com/",
        "group_above": "00000000-0000-0000-0000-000000000000"
    },
    "webhook_type": "user_updates_group"
}
```

```
user_deletes_group
```
```json
{
    "uuid": "00000000-0000-0000-0000-000000000000",
    "group": {
        "uuid": "00000000-0000-0000-0000-000000000000",
        "name": "group",
        "description": "group",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "00000000-0000-0000-0000-000000000000"
        ],
        "url": "https://www.allplayers.com/g/group",
        "logo": "https://www.allplayers.com/",
        "group_above": "00000000-0000-0000-0000-000000000000"
    },
    "webhook_type": "user_deletes_group"
}
```

```
user_adds_role
```
``json
{
    "uuid": "00000000-0000-0000-0000-000000000000",
    "group": {
        "uuid": "00000000-0000-0000-0000-000000000000",
        "name": "group",
        "description": "group",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "00000000-0000-0000-0000-000000000000"
        ],
        "logo": "https://www.allplayers.com/",
        "group_above": "00000000-0000-0000-0000-000000000000"
    },
    "member": {
        "uuid": "00000000-0000-0000-0000-000000000000",
        "group_uuid": "00000000-0000-0000-0000-000000000000",
        "group_name": "group",
        "first_name": null,
        "last_name": null,
        "join_date": "0000-00-00 00:00:00",
        "role_name": "Admin",
        "role_uuid": "00000000-0000-0000-0000-000000000000",
        "is_admin": true
    },
    "webhook_type": "user_adds_role",
    "submissions": []
}
```

```
user_removes_role
```
```json
{
    "uuid": "00000000-0000-0000-0000-000000000000",
    "group": {
        "uuid": "00000000-0000-0000-0000-000000000000",
        "name": "group",
        "description": "group",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "00000000-0000-0000-0000-000000000000"
        ],
        "url": "https://www.allplayers.com/g/group",
        "logo": "https://www.allplayers.com/",
        "group_above": "00000000-0000-0000-0000-000000000000"
    },
    "member": {
        "uuid": "00000000-0000-0000-0000-000000000000",
        "group_uuid": "00000000-0000-0000-0000-000000000000",
        "group_name": "group",
        "first_name": null,
        "last_name": null,
        "join_date": "1969-12-31 18:00:00",
        "role_name": "Player",
        "role_uuid": "00000000-0000-0000-0000-000000000000",
        "is_admin": 1
    },
    "webhook_type": "user_removes_role"
}
```

```
user_adds_submission
```
```json
{
    "uuid": "00000000-0000-0000-0000-000000000000",
    "group": {
        "uuid": "00000000-0000-0000-0000-000000000000",
        "name": "group",
        "description": "group",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "00000000-0000-0000-0000-000000000000"
        ],
        "url": "https://www.allplayers.com/g/group",
        "logo": "https://www.allplayers.com/",
        "group_above": "00000000-0000-0000-0000-000000000000"
    },
    "webform": {
        "title": "Form",
        "uuid": "00000000-0000-0000-0000-000000000000"
    },
    "webform_submission": {
        "submission_id": 1,
        "user_uuid": "00000000-0000-0000-0000-000000000000",
        "data": {
            "field_name": {
                "cid": 1,
                "value": "data"
            }
        }
    },
    "webhook_type": "user_adds_submission",
    "submissions": {
        "2038": "first"
    }
}
```


### Using a Webhook

For one example, in a [Sinatra](http://sinatra.rubyforge.org/) server, you would handle a JSON request like this:

```
post '/' do
    push = JSON.parse[:event_data])
    "I got some JSON: #{push.inspect}"
end
```

### Troubleshooting

We recommend using [RequestBin](http://requestb.in/), an external service, to tests the data received from our webhooks.

1. Visit [RequestBin](http://requestb.in/) and click 'Create a RequestBin'.
2. Copy the URL you are given
3. Open the group settings page in the Features section or in the Group Admin toolbar, once you've enabled the webhooks feature.
4. Paste the RequestBin URL in the Custom webhook section.
5. Click Save.
6. Look at the request on Requestbin by refreshing the bin page.

### Contributing

If you are interested in making changes to the Service Webhooks, please use our guide on making [contributions](https://github.com/AllPlayers/service-webhooks).
