# PromptTrace - Usage Guide

## Installation

### Option 1: Clone from GitHub
```bash
git clone https://github.com/pbsecforge-lab/PromptTrace.git
cd PromptTrace
```

### Option 2: Download ZIP
Download and extract the ZIP file from GitHub releases.

### Requirements Check
```bash
python --version  # Should be 3.7 or higher
```

## Basic Usage

### Run Full Extraction
```bash
python prompttrace.py
```

This will:
1. Scan all VS Code artifact locations
2. Extract prompts from all sources
3. Detect duplicate entries
4. Identify suspicious prompts
5. Generate reports

### Output Files

After running, you'll get:

```
UNIFIED_FORENSIC_COMPLETE_REPORT.txt  (Human-readable report)
UNIFIED_FORENSIC_COMPLETE_REPORT.json (Structured data)
```

## Understanding the Report

### Section 1: Executive Summary
- **Total Prompts**: How many unique prompts were found
- **Threat Indicators**: Critical/High risk prompts detected
- **Statistics**: Average/longest prompt lengths
- **Risk Level**: Overall assessment (CRITICAL/HIGH/MEDIUM/LOW)

### Section 2: Data Sources
- **JSONL Sessions**: Live chat files extracted
- **Forensic Dump**: Historical data recovered
- **Database**: SQLite artifacts found
- **Metadata**: Session information

Each source shows:
- ✅ Complete - Extraction successful
- ❌ No data - No artifacts found in location

### Section 3: All Extracted Prompts
Lists every prompt with:
- **Source**: Where it came from
- **Length**: Character count
- **Threat Level**: 
  - ✓ Normal (no indicators)
  - ⚠️ REVERSE SHELL (critical)
  - ⚠️ CREDENTIAL-RELATED (high)
  - ⚠️ MALWARE (high)
- **Timestamp**: When extracted
- **Content**: Full prompt text

### Section 4: Chain of Custody
Documents:
- Evidence collection date/time
- Preservation method
- Original file locations
- Data integrity verification
- Legal statement

## Threat Detection Examples

### REVERSE SHELL
```
Prompt: "write a python reverse shell"
Risk: CRITICAL
Indicates: Attacker creating command-and-control payload
```

### CREDENTIAL DUMPING
```
Prompt: "extract windows credentials from registry"
Risk: HIGH
Indicates: Stealing authentication data
```

### MALWARE DEVELOPMENT
```
Prompt: "create a keylogger in python"
Risk: HIGH
Indicates: Malicious code generation
```

## Interpreting Results

### No Artifacts Found
- VS Code not installed
- No AI extensions used
- Artifacts deleted/cleaned
- Different installation location

### Low Prompt Count
- Recent VS Code installation
- Artifacts cleared/rotated
- Limited AI assistant usage

### High Threat Count
- Suspicious activity detected
- Potential malicious intent
- Requires further investigation
- Consider incident response

## Use Cases

### Incident Response
1. Run PromptTrace on suspected system
2. Review threat indicators
3. Document findings in report
4. Correlate with other artifacts
5. Collect JSON for further analysis

### Forensic Analysis
1. Preserve original system
2. Run PromptTrace
3. Compare with baseline
4. Timeline analysis
5. Evidence preservation

### Security Audit
1. Run on user workstations
2. Generate summary reports
3. Identify policy violations
4. Track AI usage patterns
5. Documentation for compliance

## Advanced Usage

### Analyzing JSON Output

The JSON report contains:
```json
{
  "generated_at": "2026-03-12T19:17:58.xxx",
  "computer": "DESKTOP-NAME",
  "user": "username",
  "total_prompts": 51,
  "total_sessions": 4,
  "duplicates_removed": 0,
  "sources": {
    "jsonl_live": 39,
    "forensic_dump": 13,
    "database": 0
  },
  "all_prompts": [
    {
      "text": "write a python script",
      "source": "JSONL (Live)",
      "file": "filename.jsonl",
      "hash": "sha256hash",
      "priority": 1,
      "timestamp": "2026-03-12T19:17:57.xxx"
    }
  ]
}
```

### Scripting / Integration

Parse JSON in your own tools:
```python
import json

with open('UNIFIED_FORENSIC_COMPLETE_REPORT.json', 'r') as f:
    data = json.load(f)
    
print(f"Total prompts: {data['total_prompts']}")
for prompt in data['all_prompts']:
    print(f"- {prompt['text'][:50]}... ({prompt['source']})")
```

## Troubleshooting

### "No prompts found"
- Check if VS Code is installed
- Verify GitHub Copilot is active
- Ensure you've used the AI assistant
- Check artifact locations manually

### "ModuleNotFoundError"
- Run with Python 3.7+
- Verify standard library (json, sqlite3) available

### "Permission denied"
- Close VS Code before running
- Run as administrator (Windows)
- Check file permissions

### "Database locked"
- Close VS Code completely
- Stop all VS Code processes
- Try again

## Performance

PromptTrace typically:
- Scans in < 5 seconds
- Extracts 50+ prompts in < 2 seconds
- Generates reports in < 1 second
- Total runtime: 10-20 seconds

For large artifact collections (1000+ prompts):
- May take 30-60 seconds
- Memory usage typically < 100MB

## Legal Considerations

PromptTrace is for:
✅ Authorized incident response
✅ Forensic investigations
✅ Security research
✅ System administration

NOT for:
❌ Unauthorized system access
❌ Privacy violations
❌ Unauthorized data collection
❌ Illegal surveillance

## Tips & Best Practices

### Before Running
1. Verify you have authorization
2. Document system details
3. Close VS Code
4. Ensure sufficient disk space

### After Running
1. Review threat indicators
2. Document findings
3. Preserve reports
4. Hash evidence files (MD5/SHA-256)

### Data Preservation
1. Don't modify original artifacts
2. Keep reports in secure location
3. Maintain chain of custody
4. Document all actions

## Next Steps

1. Review the generated report
2. Analyze threat indicators
3. Correlate with other artifacts
4. Interview system owner
5. Escalate if needed

## Support

- Check README.md for overview
- Review CONTRIBUTING.md for guidelines
- Open GitHub issue for bugs
- Submit feature requests

---

**Remember: PromptTrace is a powerful forensic tool. Use responsibly and legally.**
