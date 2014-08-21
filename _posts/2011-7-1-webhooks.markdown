---
layout: default
title: Webhooks
---

# AllPlayers Webhooks
Every Group on AllPlayers has the ability to communicate with an external web
server via Webhooks. When a Webhook is triggered the related data, encoded in
JSON or form-urlencoded, is sent to your specified external URL. These Webhooks
can be used to update your external application using our internal data. You can
view the contents and types of available Webhooks below.

**Note:** Webhooks for a group are sent, based on the parent groups webhook
settings.

Check out the following for more information:<br>
1. <a href="#enabling-webhooks">Enabling Webhooks</a><br>
-  <a href="#types-of-Webhooks">Types of Webhooks</a><br>
-  <a href="#webhook-templates">Webhook Templates</a><br>
 -  <a href="#user_creates_group">user_creates_group</a><br>
 -  <a href="#user_updates_group">user_updates_group</a><br>
 -  <a href="#user_deletes_group">user_deletes_group</a><br>
 -  <a href="#user_adds_role">user_adds_role</a><br>
 -  <a href="#user_removes_role">user_removes_role</a><br>
 -  <a href="#user_adds_submission">user_adds_submission</a><br>
 -  <a href="#user_removed_from_group">user_removed_from_group</a><br>
 -  <a href="#user_creates_event">user_creates_event</a><br>
 -  <a href="#user_updates_event">user_updates_event</a><br>
 -  <a href="#user_deletes_event">user_deletes_event</a><br>
-  <a href="#using-a-webhook">Using a Webhook</a><br>
-  <a href="#troubleshooting">Troubleshooting</a><br>
-  <a href="#contributing">Contributing</a><br>

<br>
## <a name="#enabling-webhooks">Enabling Webhooks</a>
1. Open the Group page on AllPlayers.com, and go to the Features page:
![](../images/webhooks1.png)
- Enable the Webhooks on the Group, and then go to the Settings page:
![](../images/webhooks2.png)
- Enter your desired URL, activate the Webhook, and click on Save:
![](../images/webhooks3.png)

<br>
## <a name="#types-of-Webhooks">Types of Webhooks</a>
There are currently ten Webhooks. These include:

Webhook Name | Description
:------------ | :------------
user_creates_group | Triggered when a sub group is created.
user_updates_group | Triggered when a sub group has its settings edited.
user_deletes_group | Triggered when an admin deletes the Group.
user_adds_role | Triggered when a user is assigned a role within a sub group (e.g. A user registers for a position in a group.)
user_removes_role | Triggered when a user has an attached role removed from its account (e.g. An admin removes a role from a member within the group).
user_adds_submission | Triggered when a user registers for a role with a webform. <br><br>**Note:** The user_adds_submission webhook is sent separately from the user_adds_role webhook.
user_removed_from_group | Triggered when a user is removed from a group.
user_creates_event | Triggered when an event is created.
user_updates_event | Triggered when an event is updated.
user_deletes_event | Triggered when an event is deleted.

<br>
## <a name="#webhook-templates">Webhook Templates</a><br>
The following are examples of our Webhooks, using the JSON response option.

<br>
### <a name="#user_creates_group">user_creates_group</a>
```json
{
    "group": {
        "uuid": "1268c823-fd3b-11e3-8b92-c2fce4bc2c70",
        "name": "webhookstest",
        "description": "webhookstest",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "America/Chicago",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.allplayers.com/g/webhookstest",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "example@example.com",
        "join_date": "2014-04-16T08:58:46-05:00",
        "is_admin": true
    },
    "webhook_type": "user_creates_group"
}
```

<br>
### <a name="#user_updates_group">user_updates_group</a>
```json
{
    "group": {
        "uuid": "1268c823-fd3b-11e3-8b92-c2fce4bc2c70",
        "name": "webhookstest_nameupdate",
        "description": "webhookstest",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "America/Chicago",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.allplayers.com/g/webhookstest",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "example@example.com",
        "join_date": "2014-04-16T08:58:46-05:00",
        "is_admin": true
    },
    "webhook_type": "user_updates_group"
}
```

### <a name="#user_deletes_group">user_deletes_group</a>
```json
{
    "group": {
        "uuid": "1268c823-fd3b-11e3-8b92-c2fce4bc2c70",
        "name": "webhookstest_nameupdate",
        "description": "webhookstest",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "America/Chicago",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.allplayers.com/g/webhookstest",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "example@example.com",
        "join_date": "2014-04-16T08:58:46-05:00",
        "is_admin": true
    },
    "webhook_type": "user_deletes_group"
}
```

### <a name="#user_adds_role">user_adds_role</a>
```json
{
    "group": {
        "uuid": "1268c823-fd3b-11e3-8b92-c2fce4bc2c70",
        "name": "webhookstest_nameupdate",
        "description": "webhookstest",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "America/Chicago",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.allplayers.com/g/webhookstest",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "4fb0f6d3-d55c-11e3-80a2-c2fce4bc2c70",
        "first_name": "cfirst",
        "last_name": "clast",
        "email": "example@allplayers.net",
        "join_date": "2014-05-06T15:23:40-05:00",
        "is_admin": false,
        "guardian": {
            "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
            "email": "example@example.com",
            "first_name": "john",
            "last_name": "smith"
        },
        "role_name": "Player"
    },
    "webhook_type": "user_adds_role"
}
```

### <a name="#user_removes_role">user_removes_role</a>
```json
{
    "group": {
        "uuid": "1268c823-fd3b-11e3-8b92-c2fce4bc2c70",
        "name": "webhookstest_nameupdate",
        "description": "webhookstest",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "America/Chicago",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.allplayers.com/g/webhookstest",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "4fb0f6d3-d55c-11e3-80a2-c2fce4bc2c70",
        "first_name": "cfirst",
        "last_name": "clast",
        "email": "example@allplayers.net",
        "join_date": "2014-05-06T15:23:40-05:00",
        "is_admin": false,
        "guardian": {
            "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
            "email": "example@example.com",
            "first_name": "john",
            "last_name": "smith"
        },
        "role_name": "Player"
    },
    "webhook_type": "user_removes_role"
}
```


### <a name="#user_adds_submission">user_adds_submission</a>
```json
{
    "group": {
        "uuid": "1268c823-fd3b-11e3-8b92-c2fce4bc2c70",
        "name": "webhookstest_nameupdate",
        "description": "webhookstest",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "America/Chicago",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.allplayers.com/g/webhookstest",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "4fb0f6d3-d55c-11e3-80a2-c2fce4bc2c70",
        "first_name": "cfirst",
        "last_name": "clast",
        "email": "example@allplayers.net",
        "join_date": "2014-05-06T15:23:40-05:00",
        "is_admin": false,
        "guardian": {
            "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
            "email": "example@example.com",
            "first_name": "john",
            "last_name": "smith"
        }
    },
    "webform": {
        "title": "form1",
        "uuid": "cba9b5b2-fd3b-11e3-8b92-c2fce4bc2c70",
        "data": {
            "profile__field_firstname__profile": "cfirst",
            "profile__field_lastname__profile": "clast",
            "profile__field_email__profile": "example@allplayers.net",
            "profile__field_birth_date__profile": "1984-05-06",
            "profile__field_user_gender__profile": "1"
        }
    },
    "webhook_type": "user_adds_submission"
}
```

### <a name="#user_removed_from_group">user_removed_from_group</a>
```json
{
    "group": {
        "uuid": "2e8887bf-06cc-11e4-b1ac-c2fce4bc2c70",
        "name": "webhooktest",
        "description": "webhooktest",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "America/Chicago",
        "organization_id": [
            "4a8dca4e-cf0e-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.allplayers.com/g/webhookstest",
        "group_above": "4a8dca4e-cf0e-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "4fb0f6d3-d55c-11e3-80a2-c2fce4bc2c70",
        "first_name": "cfirst",
        "last_name": "clast",
        "email": "cfirstclast@allplayers.net",
        "join_date": "2014-05-06T15:23:40-05:00",
        "is_admin": false,
        "guardian": {
            "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
            "email": "example@example.com",
            "first_name": "john",
            "last_name": "smith"
        }
    },
    "webhook_type": "user_removed_from_group"
}
```

### <a name="#user_creates_event">user_creates_event</a>
```json
{
    "group": {
        "uuid": "1268c823-fd3b-11e3-8b92-c2fce4bc2c70",
        "name": "webhookstest_nameupdate",
        "description": "webhookstest",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "America/Chicago",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.allplayers.com/g/webhookstest",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "example@example.com",
        "join_date": "2014-04-16T08:58:46-05:00",
        "is_admin": true
    },
    "event": {
        "uuid": "285c0e5b-fd89-11e3-ac0f-c2fce4bc2c70",
        "title": "(Away Group) @ (Home Group)",
        "description": "web1/web2",
        "timezone": "America/Chicago",
        "start": "2014-06-03T18:25:00-05:00",
        "end": "2014-06-03T19:25:00-05:00",
        "location": {
            "uuid": "2de79f64-fd3e-11e3-8b92-c2fce4bc2c70",
            "title": "stadium1",
            "street": "4321 fubar lane",
            "additional": "unit baz",
            "city": "City",
            "province": "NY",
            "postal_code": "12345",
            "country": "us",
            "latitude": "42.814243",
            "longitude": "-73.939569"
        },
        "competitor": [
            {
                "uuid": "6f39fca6-fd85-11e3-ac0f-c2fce4bc2c70",
                "name": "web1",
                "label": "home",
                "score": "1"
            },
            {
                "uuid": "8f559612-fd85-11e3-ac0f-c2fce4bc2c70",
                "name": "web2",
                "label": "away",
                "score": "2"
            }
        ]
    },
    "webhook_type": "user_creates_event"
}
```

### <a name="#user_updates_event">user_updates_event</a>
```json
{
    "group": {
        "uuid": "1268c823-fd3b-11e3-8b92-c2fce4bc2c70",
        "name": "webhookstest_nameupdate",
        "description": "webhookstest",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "America/Chicago",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.allplayers.com/g/webhookstest",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "example@example.com",
        "join_date": "2014-04-16T08:58:46-05:00",
        "is_admin": true
    },
    "event": {
        "uuid": "285c0e5b-fd89-11e3-ac0f-c2fce4bc2c70",
        "title": "(Away Group) @ (Home Group)",
        "description": "web1/web2_update1",
        "timezone": "America/Chicago",
        "start": "2014-06-03T18:25:00-05:00",
        "end": "2014-06-03T19:25:00-05:00",
        "location": {
            "uuid": "2de79f64-fd3e-11e3-8b92-c2fce4bc2c70",
            "title": "stadium1",
            "street": "4321 fubar lane",
            "additional": "unit baz",
            "city": "City",
            "province": "NY",
            "postal_code": "12345",
            "country": "us",
            "latitude": "42.814243",
            "longitude": "-73.939569"
        },
        "competitor": [
            {
                "uuid": "6f39fca6-fd85-11e3-ac0f-c2fce4bc2c70",
                "name": "web1",
                "label": "home",
                "score": "1"
            },
            {
                "uuid": "8f559612-fd85-11e3-ac0f-c2fce4bc2c70",
                "name": "web2",
                "label": "away",
                "score": "2"
            }
        ]
    },
    "webhook_type": "user_updates_event"
}
```

### <a name="#user_deletes_event">user_deletes_event</a>
```json
{
    "group": {
        "uuid": "1268c823-fd3b-11e3-8b92-c2fce4bc2c70",
        "name": "webhookstest_nameupdate",
        "description": "webhookstest",
        "group_category": "Baseball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "America/Chicago",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.allplayers.com/g/webhookstest",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "example@example.com",
        "join_date": "2014-04-16T08:58:46-05:00",
        "is_admin": true
    },
    "event": {
        "uuid": "285c0e5b-fd89-11e3-ac0f-c2fce4bc2c70",
        "title": "web2 @ web1",
        "description": "web1/web2_update1",
        "timezone": "America/Chicago",
        "start": "2014-06-03T18:25:00-05:00",
        "end": "2014-06-03T19:25:00-05:00",
        "location": {
            "uuid": "2de79f64-fd3e-11e3-8b92-c2fce4bc2c70",
            "title": "stadium1",
            "street": "4321 fubar lane",
            "additional": "unit baz",
            "city": "City",
            "province": "NY",
            "postal_code": "12345",
            "country": "us",
            "latitude": "42.814243",
            "longitude": "-73.939569"
        },
        "competitor": [
            {
                "uuid": "6f39fca6-fd85-11e3-ac0f-c2fce4bc2c70",
                "name": "web1",
                "label": "home",
                "score": "1"
            },
            {
                "uuid": "8f559612-fd85-11e3-ac0f-c2fce4bc2c70",
                "name": "web2",
                "label": "away",
                "score": "2"
            }
        ]
    },
    "webhook_type": "user_deletes_event"
}
```

<br>
## <a name="#using-a-webhook">Using a Webhook</a>
For one example, in a [Sinatra](http://sinatra.rubyforge.org/) server, you would
handle a JSON request like this:

```ruby
post '/' do
    push = JSON.parse[:event_data])
    "I got some JSON: #{push.inspect}"
end
```

<br>
## <a name="#troubleshooting">Troubleshooting</a>
We recommend using [RequestBin](http://requestb.in/), an external service, to
tests the data received from our webhooks.

1. Visit [RequestBin](http://requestb.in/) and click 'Create a RequestBin'.
-  Copy the URL you are given
-  Open the group settings page in the Features section or in the Group Admin
toolbar, once you've enabled the webhooks feature.
-  Paste the RequestBin URL in the Custom webhook section.
-  Click Save.
-  Look at the request on Requestbin by refreshing the bin page.

<br>
## <a name="#contributing">Contributing</a>
If you are interested in making changes to the Service Webhooks, please use our
guide on making [contributions](https://github.com/AllPlayers/service-webhooks#steps-to-contributing).
