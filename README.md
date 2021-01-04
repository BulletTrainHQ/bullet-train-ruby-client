<img width="100%" src="https://raw.githubusercontent.com/Flagsmith/flagsmith-frontend/master/hero.png"/>

# Flagsmith Client

The SDK clients for Ruby [https://flagsmith.com/](https://www.flagsmith.com/). Flagsmith allows you to manage feature flags and remote config across multiple projects, environments and organizations.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See running in production for notes on how to deploy the project on a live system.

## Installing

### VIA gem

`gem install flagsmith`

## Usage

**Retrieving feature flags for your project**

**For full documentation visit [https://docs.flagsmith.com/](https://docs.flagsmith.com/)**

```ruby
require "flagsmith"

flagsmith = Flagsmith.new("<<Your API KEY>>")

if flagsmith.get_value("font_size")
  #    Do something awesome with the font size
end

if flagsmith.feature_enabled?("does_not_exist")
  #do something
else
  #do nothing, or something else
end

```

**Available Options**

| Property  |                                            Description                                            | Required |                     Default Value |   Environment Key |
| --------- | :-----------------------------------------------------------------------------------------------: | -------: | --------------------------------: | ----------------: |
| `api_key` |  Defines which project environment you wish to get flags for. _example ACME Project - Staging._   |  **YES** |                              null | FLAGSMITH_API_KEY |
| `url`     | Use this property to define where you're getting feature flags from, e.g. if you're self hosting. |   **NO** | https://api.flagsmith.com/api/v1/ |     FLAGSMITH_URL |

**Available Functions**

| Property                                          |                                                     Description                                                      |
| ------------------------------------------------- | :------------------------------------------------------------------------------------------------------------------: |
| `init`                                            |                                 Initialize the sdk against a particular environment                                  |
| `feature_enabled?(key)`                           |         Get the value of a particular feature e.g. `flagsmith.feature_enabled?("powerUserFeature") // true`          |
| `feature_enabled?(key, user_id, default = false)` | Get the value of a particular feature for a user e.g. `flagsmith.feature_enabled?("powerUserFeature", 1234) // true` |
| `get_value(key)`                                  |                 Get the value of a particular feature e.g. `flagsmith.get_value("font_size") // 10`                  |
| `get_value(key, user_id, default = nil)`          |    Get the value of a particular feature for a specified user e.g. `flagsmith.get_value("font_size", 1234) // 15`    |
| `get_flags()`                                     |       Trigger a manual fetch of the environment features, if a user is identified it will fetch their features       |
| `get_flags(user_id)`                              |                       Trigger a manual fetch of the environment features with a given user id                        |
| `set_trait(user_id, trait, value)`                |                                    Set the value of a trait for the given user id                                    |

**Identifying Users**

Identifying users allows you to target specific users from the [Flagsmith dashboard](https://www.flagsmith.com/).
You can include an optional user identifier as part of the `feature_enabled?` and `get_value` methods to retrieve unique user flags and variables.

## Contributing

Please read [CONTRIBUTING.md](https://gist.github.com/kyle-ssg/c36a03aebe492e45cbd3eefb21cb0486) for details on our code of conduct, and the process for submitting pull requests to us.

## Getting Help

If you encounter a bug or feature request we would like to hear about it. Before you submit an issue please search existing issues in order to prevent duplicates.

## Get in touch

If you have any questions about our projects you can email <a href="mailto:projects@solidstategroup.com">projects@solidstategroup.com</a>.

## Useful links

[Website](https://flagsmith.com)

[Documentation](https://docs.flagsmith.com/)

[YouTube Tutorials](https://www.youtube.com/channel/UCki7GZrOdZZcsV9rAIRchCw)
