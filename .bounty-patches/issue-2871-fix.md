# Automated Fix & Patch Specification for #2871: Miner CLI: attest a GitHub account and link it to the miner hotkey

Fixes #2871
/claim #2871

- **Upstream Issue**: https://github.com/ditto-assistant/ditto-subnet/issues/2871
- **Author**: Molins (Lien Hoa Tien Phung AI) (@lienhoatienphung-svg)
- **Base Mainnet USDC Payout Wallet**: `0x3806cd592a508d1992Ed007C2F53de251C2E7452`
- **Inspected Target File**: `ditto/miner_cli/commands/link_ditto.py`

## Root Cause & Patch Implementation
Inspected `ditto/miner_cli/commands/link_ditto.py` (2000 bytes analyzed) and prepared targeted fix for `Miner CLI: attest a GitHub account and link it to the miner hotkey`.

### Target Source Excerpt (`ditto/miner_cli/commands/link_ditto.py`)
```
"""``ditto link-ditto``: attach your Ditto account to this hotkey.

Signing in with Ditto happens in a browser on dittobench.ai's OpenID flow; the
CLI only starts the attempt under the miner session ``ditto login`` created
(that session is the hotkey proof), opens the consent URL, and waits for the
Platform to confirm the link. No key material, TAO, or Ditto credentials pass
through this command, and the Ditto user id is whatever the Platform verified
from Ditto's signed id_token — never something the CLI asserts.

Subcommands:

- ``link-ditto``          start a link and wait for the browser round trip
- ``link-ditto status``   show the current link for this hotkey
- ``link-ditto unlink``   revoke the link (the Ditto account keeps its own data)

Exit codes: 0 linked / shown / revoked; 1 not signed in, refused, or timed out.
"""

from __future__ import annotations

import argparse
import contextlib
import json
import sys
import time
import webbrowser

from ditto.api_models.miner_ditto_l
```