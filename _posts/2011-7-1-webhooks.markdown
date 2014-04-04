---
layout: default
title: WebHooks
---
# AllPlayers Webhooks

Every Group on AllPlayers has the option to communicate with an external web server via Webhooks. When a subgroup is created or a member is added to a subgroup, a Webhook will be triggered and sent to the specified external URL. These WebHooks can be used to update your external application using our internal data. You can view the contents of our Webhooks below.

### Enabling Webhooks
1.   Open the group page on AllPlayers.com and go to the features page
![Features](http://content.screencast.com/users/artkon/folders/Jing/media/1c985590-471c-4f5d-8f6e-6f58db65a9e7/00000030.png)
2.   Enable the webhooks on the group, and then go to the settings page
![Enable Webhooks](http://content.screencast.com/users/artkon/folders/Jing/media/4d0126f8-3192-4161-b348-445e5c693337/00000031.png)
3.   Enter your URL and click on Save
![URL Webhooks](http://content.screencast.com/users/artkon/folders/Jing/media/6be36afe-c262-490e-a504-d09ef32e3456/00000032.png)

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

For one example, you would handle a request like this, in a [Sinatra](http://sinatra.rubyforge.org/) server:

    post '/' do
      push = JSON.parse[:event_data])
      "I got some JSON: #{push.inspect}"
    end

### Troubleshooting

We recommend using [RequestBin](http://requestb.in/), an external service that tests your post-receive messages.

1.   Visit [RequestBin](http://requestb.in/) and click 'Create a RequestBin'
2.   Copy the URL you are given
3.   Open the group settings page in the features section or in the group admin toolbar once you've enabled the webhooks feature.
4.   Paste the RequestBin URL in the Custom webhook section.
5.   Click Save.
6.   Look at the request on requestbin by refreshing the bin page.

### Contributing

Use our guide on contributing using the readme on our github repo for AllPlayers Service Hooks. [Contribute](https://github.com/AllPlayers/service-webhooks)
