ChEEx
=====

Embedded Elixir templates for chat apps.

## DESCRIPTION

This is a *YET TO BE DEVELOPED* idea for developing a templating dsl for chat apps using Elixir's EEx [SmartEngine](https://github.com/elixir-lang/elixir/blob/main/lib/eex/lib/eex/smart_engine.ex).

The idea is to support multiple chat app platforms. The following come to mind as inclusive to the initial releases:

1. Slack
1. Discord
1. Microsoft Teams
1. Amazon Alexa
1. SMS

## PROPOSALS

### Support for seperate platforms

I am unsure if it is possible to define one language dsl for all but I do know that exceptions will have to be made. I am think at the very best, you could have a "ChEEx DSL" and then have exceptions for each platform, similar to something like React Native. I think it would be wise to see how it looks for various platforms and then see if there are enough commonalities to create a common engine.

#### Support via file extension

Support would look like having files for different platforms, e.g. `welcome_message.slack.cheex` and `welcome_message.discord.cheex`.

#### Support via a block inside a template

There could be support for multiple platforms within one template. The file would be `welcome_message.cheex` and would have the following content:

```
<%= :slack do %>
  <%= render slack/section text=<%= welcome_message %> %>
<% end %>

<%= :teams do %>
  <%= render teams/card body=<%= welcome_message %> %>
<% end %>
```

#### Support via a component

Even "partials" could have platform-specific files. So calling this: `<%= render "welcome_message" %>` would render `_welcome_message.slack.cheex` on Slack and `_welcome_message.teams.cheex` on Microsoft Teams.

### Slack Support

In order to get the initial templating engine running, I believe cheex should implement basic Slack component support using either a rudimentary library? I propose it supports the current blockkit with partials using an existing Phoenix templating (or similar library).

You should be able to get started with the following:

#### Layout Blocks

```
<section text="This is awesome!" />
<section text="It will automatically detect :emoji:" />
<section text="As well as *mark down*" />
<section text="As well as *mark down*">
  <accessory>
    <datepicker initial_date={@initia_date} />
  </accessory>
</section>
<section>
  <field text="" />
</section>
```

## COMMUNITY

### Contributing

1. Clone the repository `git clone https://github.com/juvet/cheex`
1. Create a feature branch `git checkout -b my-awesome-feature`
1. Codez!
1. Commit your changes (small commits please)
1. Push your new branch `git push origin my-awesome-feature`
1. Create a pull request `gh pr create --head octocat:my-awesome-feature`

## Copyright and License

Copyright (c) 2022, Jamie Wright.
