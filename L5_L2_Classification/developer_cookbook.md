# Developer Cookbook — api-oss-tools
**Stack:** Python 3.11, Click, rich, tqdm, AIOSS_FORMAT
**Domain:** Sovereign CLI toolbox: utilities for AIOSS chain management, PAX model ops, benchmarking
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```bash
# AIOSS tools
anticloud tool aioss stats ./audit.aioss        # chain stats
anticloud tool aioss export ./audit.aioss --json # export to JSON
anticloud tool aioss verify ./audit.aioss        # verify all entries

# PAX tools
anticloud tool pax --prompt 'What is the TRL of K_BRAINFLOW?' --max-tokens 128
anticloud tool pax benchmark --model ./pax-27b-q4.gguf --n-tokens 100

# Project tools
anticloud tool project list --tier TIER_7
anticloud tool project health --all
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

# After every api-oss-tools output:
chain_hash = aioss_append("./api_oss_tools.aioss",
                           result_bytes, "api-oss-tools")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all api-oss-tools operations are logged to api-oss-logging and audited by api-oss-compliance.
