[![Build Status](https://www.bitrise.io/app/c74bf2e2706c9cbb.svg?token=vWNpdgCmMqjajdHkjlokMQ&branch=master)](https://www.bitrise.io/app/c74bf2e2706c9cbb)

Sample project to test the CI-service [Bitrise](https://www.bitrise.io) with the
[Pebble build step](https://github.com/HBehrens/bitrise-step-pebble-build]).

Use this `workflow.yml` to build it

```
format_version: 1.2.0
default_step_lib_source: https://github.com/bitrise-io/bitrise-steplib.git
title: Bitrise example for Pebble
description: |-
  To use this workflow, import you Pebble project,
  add a custom workflow, and
  replace its yml with the content of this file
trigger_map:
- pattern: "*"
  is_pull_request_allowed: true
  workflow: build
workflows:
  build:
    steps:
    - git-clone@3.2.0: {}
    - git::https://github.com/HBehrens/bitrise-step-pebble-build.git@master:
        title: Pebble build
        inputs:
        - sdk_without_emulator: 'yes'
```
