#
# Vendoring Setup
#
# We create a custom `.cargo/config.toml` configuration directory with
# dependency vendoring pre-configured to the vendoring directory.
#

configure_file(
        configuration: {
                'vendordir': meson.global_source_root() / use_vendordir,
        },
        input: 'config.toml.in',
        output: 'config.toml',
)
