# ip_sniffer

A small multi-threaded TCP port scanner written in Rust.

Features
- Distributes port ranges across threads (default 4 threads).
- Uses a per-connection timeout to avoid blocking (1s by default).

Build

```bash
cargo build --release
```

Run / Usage

- Scan with default threads:

```bash
cargo run -- 127.0.0.1
```

- Specify number of threads with `-j`:

```bash
cargo run -- -j 100 192.168.1.1
```

- Show help:

```bash
cargo run -- -h
cargo run -- -help
```

Behavior
- The program prints a dot `.` when it finds an open port during scanning, then lists open ports after the scan completes.
- Scans ports 1..65535; runtime depends on number of threads and network latency.

Notes and tips
- Scanning a remote host may be slow; increase `-j` to speed up but be mindful of network limits and target policies.
- You can change the per-connection timeout in `src/main.rs` if you need a shorter or longer wait.

Files
- The scanner entrypoint is `src/main.rs`.
