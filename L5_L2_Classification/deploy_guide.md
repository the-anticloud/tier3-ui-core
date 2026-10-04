# Deploy Guide — ui-core
**Platform:** Anticloud sovereign infrastructure | Air-gap capable
**Stack:** TypeScript, React 18, Tailwind CSS (local build), AIOSS_FORMAT (for UI action audit)

## Prerequisites
Python 3.11+. See stack: TypeScript, React 18, Tailwind CSS (local build), AIOSS_FORMAT (for UI action audit). AIOSS_FORMAT required. PAX 27B weights for AI-assisted features.

## AIOSS Integration
```bash
aioss init --module ui-core --output ./ui_core.aioss
aioss append --chain ./ui_core.aioss --payload ./output.bin --module ui-core
aioss verify --chain ./ui_core.aioss
```

## Air-Gap Deployment
```bash
# On networked machine:
pip download -r requirements.txt -d ./wheels/
# Transfer wheels/ to air-gap host, then:
pip install --no-index --find-links ./wheels/ -r requirements.txt
```

## PAX 27B Harness Wiring
```python
from anticloud_pax import PAXHarness
harness = PAXHarness(
    model_path="./pax-27b-q4.gguf",
    module="ui-core",
    aioss_chain="./ui_core.aioss",
    classification="L5_NARROW_L2_GENERAL"
)
result = harness.process(input_data)
```

## Verification
```bash
aioss verify --chain ./ui_core.aioss --verbose
python -m ui_core.tests.smoke
```
