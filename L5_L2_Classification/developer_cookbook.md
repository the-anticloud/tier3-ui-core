# Developer Cookbook — ui-core
**Stack:** TypeScript, React 18, Tailwind CSS (local build), AIOSS_FORMAT (for UI action audit)
**Domain:** Sovereign UI component library: design system for all Anticloud web interfaces
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```typescript
import { AIChainPanel, MetricBadge, TerminalOutput } from '@anticloud/ui-core';

// Real-time chain display
<AIChainPanel
  chainHash={currentChainHash}
  entryCount={chainEntries}
  lastVerified={lastVerified}
  onVerify={() => verifyChain()}
/>

// Metric badges (gold/green Anticloud theme)
<MetricBadge label="tok/s" value={97.3} status="green" />
<MetricBadge label="AIOSS overhead" value="0.8ms" status="gold" />
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every ui-core output:
chain_hash = aioss_append("./ui_core.aioss",
                           result_bytes, "ui-core")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all ui-core operations are logged to api-oss-logging and audited by api-oss-compliance.
