# *******************************************************************************
# Copyright (c) 2026 Contributors to the Eclipse Foundation
#
# See the NOTICE file(s) distributed with this work for additional
# information regarding copyright ownership.
#
# This program and the accompanying materials are made available under the
# terms of the Apache License Version 2.0 which is available at
# https://www.apache.org/licenses/LICENSE-2.0
#
# SPDX-License-Identifier: Apache-2.0
# *******************************************************************************

load("//bazel/tools:json_schema_validator.bzl", "validate_json_schema_test")

exports_files(["crypto_config.json"])

validate_json_schema_test(
    name = "validate_crypto_config_schema",
    json = "crypto_config.json",
    schema = "//score/crypto/src/daemon/config:crypto_fbs_to_json_schema",
    tags = ["lint"],
    target_compatible_with = ["@platforms//os:linux"],
)
