---
created: 2026-04-02T08:37:21+08:00
modified: 2026-04-02T09:26:16+08:00
---

# Rust static build

https://zhuanlan.zhihu.com/p/25127947378?share_code=1cHiUDr82Tlhx&utm_psn=2022968024261558383

---

For Rust projects, using musl is the most straightforward and recommended way to create a fully static binary that eliminates glibc dependencies.

While it is technically possible to statically link glibc, this approach is not recommended for most use cases.

Here are the two primary methods to solve this.

### 1. The Recommended Way: Target `musl`

This approach compiles your project with `musl libc`, a lightweight alternative to glibc, and statically links it into your binary. The result is a portable binary that will run on almost any Linux distribution.

1.  **Add the musl target**: Add the target for your architecture (e.g., `x86_64-unknown-linux-musl` for 64-bit) using `rustup`.
    ```bash
    rustup target add x86_64-unknown-linux-musl
    ```

2.  **Build your project**: Use `cargo build` with the `--target` flag.
    ```bash
    cargo build --release --target x86_64-unknown-linux-musl
    ```

3.  **Install musl tools (if needed)**: If you get linker errors, you may need to install the `musl-tools` package.
    ```bash
    sudo apt install musl-tools  # Debian/Ubuntu
    ```

### 2. The Alternative: Statically Link `glibc`

Rust can also attempt to statically link `glibc` using the `+crt-static` target feature. However, this method is complex and has significant pitfalls:

*   **Incomplete static linking**: A statically linked glibc may still dynamically load other libraries (e.g., for NSS) at runtime, creating hard-coded paths that can fail on other distros.
*   **Cannot produce a cdylib**: This feature cannot be used to create a dynamic system library (a `.so` file) on Linux.
*   **Requires static glibc library**: You must install the static version of glibc (e.g., `libc6-dev` on Ubuntu), which is often not present by default.

If you still want to try this, configure your project with a `.cargo/config.toml` file:
```toml
[target.x86_64-unknown-linux-gnu]
rustflags = ["-C", "target-feature=+crt-static"]
```

### Verify Your Build

To confirm you have successfully created a static binary, use the `ldd` command. A fully static binary will output `not a dynamic executable` instead of listing shared libraries.
```bash
ldd target/x86_64-unknown-linux-musl/release/your_app
```

### Additional Optimization (Optional)

To further reduce the size of your static binary, you can add the following optimizations to your `Cargo.toml` file. This is especially useful for musl binaries:
```toml
[profile.release]
lto = true          # Link-time optimization
panic = "abort"     # Abort on panic, instead of stack unwinding
strip = true        # Remove debug symbols
codegen-units = 1   # Improves optimization at the cost of compile time
```

### Alternative: Use `cross` for Easy Containerized Builds

If managing toolchains is complex, consider using `cross`, which handles the setup for musl or other targets inside Docker containers.

*   Install: `cargo install cross`
*   Build: `cross build --target x86_64-unknown-linux-musl --release`

***

In summary, for a robust solution to bundle all C dependencies, use the `x86_64-unknown-linux-musl` target. It is the only method that reliably produces a truly standalone binary without the compatibility risks associated with static glibc linking.
