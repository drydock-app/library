FROM rust:latest
RUN cargo install --git https://github.com/paritytech/cachepot
FROM rust:latest as run
LABEL org.opencontainers.image.source https://github.com/drydock-app/library
COPY --from=build /usr/local/cargo/bin/cachepot /usr/local/cargo/bin/cachepot
