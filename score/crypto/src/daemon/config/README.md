<!-- ----------------------------------------------------------------------------
  Copyright (c) 2026 Contributors to the Eclipse Foundation

  See the NOTICE file(s) distributed with this work for additional
  information regarding copyright ownership.

  This program and the accompanying materials are made available under the
  terms of the Apache License Version 2.0 which is available at
  https://www.apache.org/licenses/LICENSE-2.0

  SPDX-License-Identifier: Apache-2.0
----------------------------------------------------------------------------- -->

# Crypto daemon configuration: FlatBuffers and JSON workflow

## What is supported

1. The FlatBuffers schema file (`.fbs`). present in ``score/crypto/src/daemon/config/crypto_config.fbs``.
2. Convert the `.fbs` to a JSON Schema. Use `bazel build //score/crypto/src/daemon/config:crypto_fbs_to_json_schema`.
3. JSON config files.
   example : ``score/crypto/tests/cert_management/config/cert_management_test_config.json`` etc.
4. Validate the JSON config against the JSON Schema : defered for now, is already handled by point 5 below.
5. Generate a FlatBuffers binary from the `.fbs` and the JSON config : accomplished by using ``flatc`` command, bazel rule is invoking it in the repo. ex. ``bazel build //score/crypto/tests/key_management/config:generate_key_management_test_config``

## Potential future extensions

6. Generate a FlatBuffers binary from the JSON Schema and the JSON config : Do we need this ?

### Open points

1. decision on naming format for generated flatbuffer bin files.


Concept for configuration for score::crypto
============================================


Goals
======
1. Concept shall align with stakeholder requirements, central concept and decision records of eclipse score.
2. Shall be extensible for the vendor distributions.
3. Loose coupling with user applications.
4. Ease of use : there shall be possibility of fallback default values, which the integrator/ user can reuse across applications instead of focrcing to configure for every application.
5. Cross Module accessibility.

Goals of Config Parser
=======================
1. Shall support reparsing and reloading of the config.
2. Individual logical group of config shall be broken into seperate classes, in order not to force clients not to depend on config which they do not need.

Stakeholder requirements
========================

1. Decisioon record : https://eclipse-score.github.io/score/main/features/configuration/config_model/index.html#doc__configuration_model
