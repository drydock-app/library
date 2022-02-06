FROM rust:latest as build
RUN rustup target add wasm32-unknown-unknown
RUN cargo install wasm-pack
FROM rust:latest
LABEL org.opencontainers.image.source https://github.com/drydock-app/library
COPY --from=build /usr/local/cargo/bin/wasm-pack /usr/local/cargo/bin/wasm-pack
