licenses(["notice"])  # Apache 2

load(
    "//bazel:envoy_build_system.bzl",
    "envoy_cc_fuzz_test",
    "envoy_cc_test",
    "envoy_package",
    "envoy_proto_library",
)

envoy_package()

envoy_cc_test(
    name = "config_impl_test",
    srcs = ["config_impl_test.cc"],
    deps = [
        ":route_fuzz_proto_cc",
        "//source/common/config:metadata_lib",
        "//source/common/config:rds_json_lib",
        "//source/common/http:header_map_lib",
        "//source/common/http:headers_lib",
        "//source/common/json:json_loader_lib",
        "//source/common/router:config_lib",
        "//source/extensions/filters/http/common:empty_http_filter_config_lib",
        "//test/fuzz:utility_lib",
        "//test/mocks/server:server_mocks",
        "//test/test_common:environment_lib",
        "//test/test_common:registry_lib",
        "//test/test_common:utility_lib",
    ],
)

envoy_proto_library(
    name = "header_parser_fuzz_proto",
    srcs = ["header_parser_fuzz.proto"],
    deps = [
        "//test/fuzz:common_proto",
        "@envoy_api//envoy/api/v2/core:base_export",
    ],
)

envoy_cc_fuzz_test(
    name = "header_parser_fuzz_test",
    srcs = ["header_parser_fuzz_test.cc"],
    corpus = "header_parser_corpus",
    deps = [
        ":header_parser_fuzz_proto_cc",
        "//source/common/http:header_map_lib",
        "//source/common/router:header_parser_lib",
        "//test/fuzz:utility_lib",
    ],
)

envoy_cc_test(
    name = "rds_impl_test",
    srcs = ["rds_impl_test.cc"],
    deps = [
        "//source/common/config:filter_json_lib",
        "//source/common/config:utility_lib",
        "//source/common/http:message_lib",
        "//source/common/json:json_loader_lib",
        "//source/common/router:rds_lib",
        "//source/server/http:admin_lib",
        "//test/mocks/init:init_mocks",
        "//test/mocks/local_info:local_info_mocks",
        "//test/mocks/server:server_mocks",
        "//test/mocks/thread_local:thread_local_mocks",
        "//test/mocks/upstream:upstream_mocks",
        "//test/test_common:utility_lib",
    ],
)

envoy_cc_test(
    name = "retry_state_impl_test",
    srcs = ["retry_state_impl_test.cc"],
    deps = [
        "//source/common/http:header_map_lib",
        "//source/common/router:retry_state_lib",
        "//source/common/upstream:resource_manager_lib",
        "//test/mocks/router:router_mocks",
        "//test/mocks/runtime:runtime_mocks",
        "//test/mocks/upstream:upstream_mocks",
        "//test/test_common:utility_lib",
    ],
)

envoy_proto_library(
    name = "route_fuzz_proto",
    srcs = ["route_fuzz.proto"],
    deps = [
        "//test/fuzz:common_proto",
        "@envoy_api//envoy/api/v2:rds_export",
    ],
)

envoy_cc_fuzz_test(
    name = "route_fuzz_test",
    srcs = ["route_fuzz_test.cc"],
    corpus = "route_corpus",
    deps = [
        ":route_fuzz_proto_cc",
        "//source/common/router:config_lib",
        "//test/fuzz:utility_lib",
        "//test/mocks/server:server_mocks",
    ],
)

envoy_cc_test(
    name = "router_ratelimit_test",
    srcs = ["router_ratelimit_test.cc"],
    deps = [
        "//source/common/http:header_map_lib",
        "//source/common/json:json_loader_lib",
        "//source/common/router:config_lib",
        "//source/common/router:router_ratelimit_lib",
        "//test/mocks/http:http_mocks",
        "//test/mocks/ratelimit:ratelimit_mocks",
        "//test/mocks/router:router_mocks",
        "//test/mocks/server:server_mocks",
        "//test/test_common:utility_lib",
        "@envoy_api//envoy/api/v2:rds_cc",
    ],
)

envoy_cc_test(
    name = "router_test",
    srcs = ["router_test.cc"],
    deps = [
        "//source/common/buffer:buffer_lib",
        "//source/common/network:utility_lib",
        "//source/common/router:router_lib",
        "//source/common/upstream:upstream_includes",
        "//source/common/upstream:upstream_lib",
        "//test/common/http:common_lib",
        "//test/mocks/http:http_mocks",
        "//test/mocks/local_info:local_info_mocks",
        "//test/mocks/network:network_mocks",
        "//test/mocks/router:router_mocks",
        "//test/mocks/runtime:runtime_mocks",
        "//test/mocks/ssl:ssl_mocks",
        "//test/mocks/upstream:upstream_mocks",
        "//test/test_common:environment_lib",
        "//test/test_common:test_time_lib",
        "//test/test_common:utility_lib",
    ],
)

envoy_cc_test(
    name = "router_upstream_log_test",
    srcs = ["router_upstream_log_test.cc"],
    external_deps = ["abseil_optional"],
    deps = [
        "//source/common/buffer:buffer_lib",
        "//source/common/config:filter_json_lib",
        "//source/common/network:utility_lib",
        "//source/common/router:router_lib",
        "//source/common/upstream:upstream_includes",
        "//source/common/upstream:upstream_lib",
        "//source/extensions/access_loggers/file:config",
        "//test/common/http:common_lib",
        "//test/mocks/access_log:access_log_mocks",
        "//test/mocks/filesystem:filesystem_mocks",
        "//test/mocks/http:http_mocks",
        "//test/mocks/local_info:local_info_mocks",
        "//test/mocks/network:network_mocks",
        "//test/mocks/router:router_mocks",
        "//test/mocks/runtime:runtime_mocks",
        "//test/mocks/server:server_mocks",
        "//test/mocks/ssl:ssl_mocks",
        "//test/mocks/upstream:upstream_mocks",
        "//test/test_common:utility_lib",
        "@envoy_api//envoy/config/filter/http/router/v2:router_cc",
    ],
)

envoy_cc_test(
    name = "shadow_writer_impl_test",
    srcs = ["shadow_writer_impl_test.cc"],
    deps = [
        "//source/common/http:headers_lib",
        "//source/common/http:message_lib",
        "//source/common/router:shadow_writer_lib",
        "//test/mocks/upstream:upstream_mocks",
    ],
)

envoy_cc_test(
    name = "header_formatter_test",
    srcs = ["header_formatter_test.cc"],
    deps = [
        "//source/common/config:metadata_lib",
        "//source/common/config:rds_json_lib",
        "//source/common/router:header_formatter_lib",
        "//source/common/router:header_parser_lib",
        "//source/common/router:string_accessor_lib",
        "//source/common/stream_info:filter_state_lib",
        "//test/common/stream_info:test_int_accessor_lib",
        "//test/mocks/http:http_mocks",
        "//test/mocks/upstream:upstream_mocks",
        "//test/test_common:utility_lib",
    ],
)

envoy_cc_test(
    name = "string_accessor_impl_test",
    srcs = ["string_accessor_impl_test.cc"],
    deps = [
        "//source/common/router:string_accessor_lib",
    ],
)
