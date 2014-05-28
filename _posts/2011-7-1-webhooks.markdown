---
layout: default
title: Webhooks
---
# AllPlayers Webhooks

Every Group on AllPlayers has the ability to communicate with an external web server via Webhooks. When a Webhook is triggered the related data, encoded in JSON or form-urlencoded, is sent to your specified external URL. These Webhooks can be used to update your external application using our internal data. You can view the contents and types of available Webhooks below.

**Note:** Webhooks for a group are sent, based on the parent group webhook settings.

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
user_removes_role | Triggered when a user has an attached role removed from its account (eg. An admin removes a role from a member within the group).
user_adds_submission | Triggered when a user registers for a role with a webform. **Note:** The user_adds_submission webhook is separate from user_adds_role.

### Webhook Templates

The following are examples of our Webhooks, using the JSON response option.


#### user_creates_group
```json
{
    "group": {
        "uuid": "a5601bd6-e670-11e3-9e7c-c2fce4bc2c70",
        "name": "demo",
        "description": "demo",
        "group_category": "Basketball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.example.com/g/demo",
        "logo": "https://www.example.com/",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "email@example.com",
        "join_date": "2014-04-16 08:58:46",
        "is_admin": true
    },
    "webhook_type": "user_creates_group"
}
```

#### user_updates_group
```json
{
    "group": {
        "uuid": "a5601bd6-e670-11e3-9e7c-c2fce4bc2c70",
        "name": "demo_name change",
        "description": "demo",
        "group_category": "Basketball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.example.com/g/demo",
        "logo": "https://www.example.com/",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "email@example.com",
        "join_date": "2014-04-16 08:58:46",
        "is_admin": true
    },
    "webhook_type": "user_updates_group"
}
```

#### user_deletes_group
```json
{
    "group": {
        "uuid": "a5601bd6-e670-11e3-9e7c-c2fce4bc2c70",
        "name": "demo_name change",
        "description": "demo",
        "group_category": "Basketball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.example.com/g/d",
        "logo": "https://www.example.com/",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "email@example.com",
        "join_date": "2014-04-16 08:58:46",
        "is_admin": true
    },
    "webhook_type": "user_deletes_group"
}
```

#### user_adds_role
```json
{
    "group": {
        "uuid": "a5601bd6-e670-11e3-9e7c-c2fce4bc2c70",
        "name": "demo",
        "description": "demo",
        "group_category": "Basketball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.example.com/g/d",
        "logo": "https://www.example.com/",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "email@example.com",
        "join_date": "2014-04-16 08:58:46",
        "is_admin": true,
        "role_name": "Player"
    },
    "webhook_type": "user_adds_role"
}
```

#### user_removes_role
```json
{
    "group": {
        "uuid": "a5601bd6-e670-11e3-9e7c-c2fce4bc2c70",
        "name": "demo_name change",
        "description": "demo",
        "group_category": "Basketball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.example.com/g/d",
        "logo": "https://www.example.com/",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "email@example.com",
        "join_date": "2014-04-16 08:58:46",
        "is_admin": true,
        "role_name": "Player"
    },
    "webhook_type": "user_removes_role"
}
```


#### user_adds_submission
```json
{
    "group": {
        "uuid": "a5601bd6-e670-11e3-9e7c-c2fce4bc2c70",
        "name": "demo",
        "description": "demo",
        "group_category": "Basketball",
        "group_type": "Team",
        "postalcode": "12345",
        "timezone": "-6:00",
        "organization_id": [
            "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
        ],
        "url": "https://www.example.com/g/d",
        "logo": "https://www.example.com/",
        "group_above": "a34a2105-c576-11e3-acdb-c2fce4bc2c70"
    },
    "member": {
        "uuid": "3ad97be5-c56f-11e3-acdb-c2fce4bc2c70",
        "first_name": "first",
        "last_name": "last",
        "email": "email@example.com",
        "join_date": "2014-04-16 08:58:46",
        "is_admin": true
    },
    "webform": {
        "title": "form1",
        "uuid": "f7703466-e670-11e3-9e7c-c2fce4bc2c70",
        "data": {
            "profile__field_firstname__profile": "first_form",
            "profile__field_lastname__profile": "last_form",
            "profile__field_email__profile": "email@example.com",
            "profile__field_birth_date__profile": "1984-04-17",
            "profile__field_user_gender__profile": "2",
            "profile__field_phone__profile": "1111111111",
            "profile__field_phone_cell__profile": "2222222222",
            "profile__field_work_number__profile": "3333333333",
            "profile__field_home_address_street__profile": "address 1_1",
            "profile__field_home_address_additional__profile": "address1_2",
            "profile__field_home_address_city__profile": "city",
            "profile__field_home_address_province__profile": "NY",
            "profile__field_home_address_postal_code__profile": "12345",
            "profile__field_home_address_country__profile": "us"
        }
    },
    "webhook_type": "user_adds_submission"
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
