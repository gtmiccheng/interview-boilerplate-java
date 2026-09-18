# Interview Boilerplate - Java

## To run tests

```bash
./gradlew build
```

## Known Issues

### When you encounter Cloudflare Warp CA Cert issues:

Error:

```
PKIX path building failed: ... unable to find valid certification path to requested target
PKIX path validation failed: ... Path does not chain with any of the trust anchors
```

Run:

```
JAVA_HOME=/path/to/your/JVM/install
"$JAVA_HOME/bin/keytool" -import -file "${HOME}/.config/cloudflare/Cloudflare_CA.pem" -alias CloudflareRootCA -keystore "${JAVA_HOME}/lib/security/cacerts" -storepass changeit -trustcacerts -noprompt
```

Add these to your `~/.zshrc`:

```
export JAVA_HOME="$(mise where java)"
export JAVA_TOOL_OPTIONS="-Djavax.net.ssl.trustStore=${JAVA_HOME}/lib/security/cacerts"
```
