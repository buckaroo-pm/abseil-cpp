load('//:subdir_glob.bzl', 'subdir_glob')
load('//:buckaroo_macros.bzl', 'buckaroo_deps')

cxx_library(
  name = 'abseil',
  header_namespace = 'absl',
  exported_headers = subdir_glob([
    ('absl', '**/*.h'),
    ('absl', '**/*.inc'),
  ]),
  srcs = glob([
    'absl/**/*.cc',
  ], exclude = glob([
    'absl/synchronization/internal/mutex_nonprod.cc',
    'absl/random/internal/named_generator.cc',
    'absl/**/*_test.cc',
    'absl/**/*_test_*.cc',
    'absl/**/*_testing.cc',
    'absl/**/*_benchmark.cc',
    'absl/**/benchmarks.cc',
    'absl/**/*_benchmark_*.cc',
  ])),
  licenses = [
    'LICENSE',
  ],
  deps = buckaroo_deps(),
  visibility = [
    'PUBLIC',
  ],
)

cxx_test(
  name = 'tests',
  header_namespace = '',
  srcs = glob([
    'absl/**/*_test.cc',
    'absl/**/*_test_*.cc',
  ]),
  preprocessor_flags = [
    '-DABSL_MALLOC_EXTENSION_TEST_ALLOW_MISSING_EXTENSION=1',
  ],
  deps = [
    ':abseil',
  ],
)
