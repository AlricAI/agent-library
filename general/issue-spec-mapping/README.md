# ISSUE SPEC MAPPING

> **Fast reference: Which spec goes with which issue?

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Quick Issue-to-Spec Mapping Guide

**Fast reference: Which spec goes with which issue?**

**Last Updated**: 2025-11-30

---

## P0-Critical Enhancements

### Issue #124: SIEM Telemetry Export Pipeline

**GitHub Issue**: https://github.com/rysweet/AzureHayMaker/issues/124

**Implementation Spec**: [`specs/SIEM_TELEMETRY_EXPORT.md`](../specs/SIEM_TELEMETRY_EXPORT.md) (80KB)

**Starter Code**: [`examples/siem_export_starter.py`](../examples/siem_export_starter.py)

**Key Files to Modify**:
- `src/azure_haymaker/knowledge_worker/telemetry/exporter.py` (NEW)
- `src/azure_haymaker/knowledge_worker/telemetry/normalizer.py` (NEW)
- `src/azure_haymaker/knowledge_worker/telemetry/connectors/` (NEW directory)

**Tests Required**:
- `tests/unit/test_siem_export.py` (NEW)
- `tests/unit/test_event_normalizer.py` (NEW)
- `tests/integration/test_siem_connectors.py` (NEW)

**Dependencies**: PR #119 (must merge first)

**Timeline**: 2.5-3.5 weeks

**ROI**: 120% | **Payback**: 5.4 months

---

### Issue #125: Windows VM Security Hardening

**GitHub Issue**: https://github.com/rysweet/AzureHayMaker/issues/125

**Implementation Spec**: [`specs/WINDOWS_VM_SECURITY_HARDENING.md`](../specs/WINDOWS_VM_SECURITY_HARDENING.md) (19KB)

**Starter Code**: [`examples/windows_vm_security_starter.py`](../examples/windows_vm_security_starter.py)

**Key Files to Modify**:
- `src/azure_haymaker/knowledge_worker/endpoints/windows_vm.py` (EXISTING - security fixes)

**Tests Required**:
- `tests/security/test_windows_vm_security.py` (NEW)
- Update: `tests/unit/test_windows_vm.py` (EXISTING)

**Dependencies**: None (can start immediately)

**Timeline**: 1-2 weeks

**ROI**: 1,165% | **Payback**: Immediate

**Blocking**: PR #121, PR #123 (this issue blocks them)

---

## P1-High Enhancements

### Issue #126: Multi-Tenant Resource Isolation

**GitHub Issue**: https://github.com/rysweet/AzureHayMaker/issues/126

**Implementation Spec**: Documented in [Enhancement Roadmap](ENHANCEMENT_ROADMAP.md) - Full spec 

*[truncated — see source for full prompt]*