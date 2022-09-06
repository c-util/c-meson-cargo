#
# Global Project Setup
#

project(
        'c-meson-cargo',
        'c',
        license: 'Apache',
        meson_version: '>=0.60.0',
        version: '1.0.0',
)
project_description = 'Meson Integration of Cargo based Rust Code'

#
# Dependency Resolution
#

bin_cargo = find_program(
        'cargo',
        native: true,
        required: true,
        version: '>=1.63',
)
bin_cp = find_program(
        'cp',
        native: true,
        required: true,
)
bin_jq = find_program(
        'jq',
        native: true,
        required: true,
        version: '>=1.6',
)

bin_build = find_program(
        './src/build.sh',
        native: true,
        required: true,
)
bin_dist = find_program(
        './src/dist.sh',
        native: true,
        required: true,
)
bin_vendor = find_program(
        './src/vendor.sh',
        native: true,
        required: true,
)

#
# Config: profile
#

use_profile = get_option('profile')

#
# Config: target
#

use_target = get_option('target')

#
# Config: vendor
#

use_vendor = get_option('vendor')
if use_vendor == 'auto'
        use_wrap_mode = get_option('wrap_mode')
        use_vendor = use_wrap_mode == 'nodownload' ? 'yes' : 'no'
endif

#
# Config: vendordir
#

use_vendordir = get_option('vendordir')

#
# Custom Build Target Skeleton
#

target_dict_build = {
        'build_always_stale': true,
        'console': true,
        'env': {
                'MCARGO_BIN_CARGO': bin_cargo.full_path(),
                'MCARGO_BIN_CP': bin_cp.full_path(),
                'MCARGO_BIN_JQ': bin_jq.full_path(),
                'MCARGO_OFFLINE': use_vendor,
                'MCARGO_TARGET_DIR': meson.project_build_root() / 'cargo-target',
                'MCARGO_VENDOR_DIR': meson.global_source_root() / use_vendordir,
        } + (use_profile == '' ? {} : {
                'MCARGO_PROFILE': use_profile,
        }) + (use_target == '' ? {} : {
                'MCARGO_TARGET': use_target,
        }),
        'command': [
                bin_build, '@OUTDIR@', '@INPUT0@',
        ],
}

#
# Vendoring Target
#

target_cmd_vendor = [bin_vendor]
target_dict_vendor = {
        'env': {
                'MCARGO_BIN_CARGO': bin_cargo.full_path(),
                'MCARGO_VENDOR_DIR': meson.global_source_root() / use_vendordir,
        },
}

#
# Custom Dist Target Skeleton
#

target_cmd_dist = [bin_dist, bin_cargo.full_path(), use_vendordir]
