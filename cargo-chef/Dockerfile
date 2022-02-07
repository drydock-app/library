FROM rust:latest as build
RUN cargo install cargo-chef --locked
FROM rust:latest as run
LABEL org.opencontainers.image.source https://github.com/drydock-app/library
COPY --from=build /usr/local/cargo/bin/chef /usr/local/cargo/bin/chef
RUN cargo chef --help
