# Changelog

## 1.1.4
- Build fix: Material3 back to the stable BOM version (the alpha broke compilation); workflow simplified.

## 1.1.3
- Fast IPv6 fallback (Settings > Advanced, on by default): no IPv6 address on the tunnel, so apps like Telegram fall back to IPv4 at once.
- A stream that dies while opening is retried once; apps wait up to 10 s for a tunnel that is reconnecting.
- Faster re-dial after the tunnel is declared unhealthy; idle connections stay open for 20 minutes.
- Recent logs section on the home screen.

## 1.1.2
- Bypass Iranian apps: package prefix `ir.`, well-known Iranian packages, bank/payment names, Persian-labelled user apps.

## 1.1.0
- Tools card: speed test, fastest server, copy exit IP.

## 1.0.8
- Creator badge.
- Faster dead-link detection (keep-alive), a 403 for one destination no longer invalidates the whole session,
  shorter refusal cache, larger relay buffer.
