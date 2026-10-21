# eMudhra dependency security patch — 2026-10-21

**repo:** openfang-fork

**scope:** eMudhra certificate trust dependency fixes

**review:** Independent read-only review: Code 9.5/10, Design 9.5/10, zero open MAJOR/MEDIUM dependency findings.

**validation:** 2251 library unit tests passed with cargo test --locked --workspace --lib.

**limitations:** Review covers source dependency changes; installed desktop binaries and live platform runtimes require separate deployment verification.

**carry:** Legacy webpki0.102.8 remains only as rumqttc error type; authentication uses patched0.103.16. Parallel environment-variable test race resolved by serial test execution. Pre-existing MQTT TLS flag handling is outside this dependency patch.

Reproduce: `cargo test --locked --workspace --lib -j2 -- --test-threads=1`. Parallel execution exposed a test environment-variable race; the serial full suite passed. Evidence: `work/logs/openfang-fork-serial-tests.log` in the security workspace.
