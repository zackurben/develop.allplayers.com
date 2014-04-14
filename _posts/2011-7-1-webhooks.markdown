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

1. user_creates_group
   - Triggered when a sub group is created.
2. user_updates_group
   - Triggered when a sub group has its settings edited.
3. user_deletes_group
   - Triggered when an admin deletes the Group.
4. user_adds_role
   - Triggered when a user is assigned a role within a sub group (eg. A user registers for a position in a group.)
5. user_removes_role
   - Triggered when a user has an attached role removed from its account (eg. A admin removes a role from a member within the group).
6. user_adds_submission
   - Triggered when a user registers for a role and the role has a webform. When the webform is filled out and submitted along with the users registration, the user_adds_submission webhook gets called.

### Webhook Templates

The following are examples of our Webhooks, using the JSON response option.

```
user_creates_group
```

```
user_updates_group
```

```
user_deletes_group
```

```
user_adds_role
```

```
user_removes_role
```

```
user_adds_submission
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
