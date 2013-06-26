---
layout: default
title: WebHooks
---
# Post-Receive Hooks

Every Group on AllPlayers has the option to communicate with a web server whenever a subgroup or a member is added to the group. These "WebHooks" can be used to update an external application.

### Adding a webhook
1.   Open the group page on AllPlayers.com and go to the features page
2.   Enable the webhooks on the group, and then go to the settings page
3.   Enter your URL and click on Save

### The member and group data

When a new subgroup gets created, we'll POST to your URL with a payload of JSON-encoded data about the group. Here's the template:

<script src="https://gist.github.com/arturo-c/5868677.js"></script>

Similarly, when a user gets assigned a role in a group, we'll POST to your URL with a payload of JSON-encoded data about the member and the group. Here's the template:

<script src="https://gist.github.com/arturo-c/5869554.js"></script>

So, for example, you'd do something like this in a [Sinatra](http://sinatra.rubyforge.org/) server:

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
