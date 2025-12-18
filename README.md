# greyvault-core
Blockchain-verified compliance infrastructure for aerospace and critical systems. Smart contracts deployed on Optimism providing real-time threat scoring, immutable audit trails, and cryptographic proof of security posture. Federal contractor ready
# Greyvault Core

Blockchain-verified compliance infrastructure protecting aerospace and critical systems. Live on Optimism mainnet.

## Overview

Greyvault Core provides immutable, cryptographically-verified proof of security compliance for enterprises requiring continuous risk assessment. Our smart contracts create an unchallengeable audit trail that transforms cyber insurance from quarterly assessments to real-time verification.

## Deployed Contracts (Optimism Mainnet)

| Contract | Address | Explorer |
|----------|---------|----------|
| GreyvaultRegistry | `0x8D735b4C1C29f783B2F8F6682899169506E0209a` | [View on Optimism](https://optimistic.etherscan.io/address/0x8D735b4C1C29f783B2F8F6682899169506E0209a) |
| GreyvaultThreatTM | `0x56125d436d3a0f3692FA4C21d7259Ca05f39f875` | [View on Optimism](https://optimistic.etherscan.io/address/0x56125d436d3a0f3692FA4C21d7259Ca05f39f875) |
| GreyvaultCompliance | `0xDF81FE0fcd15a7FbAa2F5a1c81fEE6b474C5a061` | [View on Optimism](https://optimistic.etherscan.io/address/0xDF81FE0fcd15a7FbAa2F5a1c81fEE6b474C5a061) |

## Architecture

┌─────────────────┐ ┌──────────────────┐ ┌───────────────────┐ │ TrustCore API │────▶│ Greyvault Core │────▶│ Optimism L2 │ │ Threat Scoring │ │ Smart Contracts │ │ Verification │ └─────────────────┘ └──────────────────┘ └───────────────────┘ │ ▼ ┌──────────────────────┐ │ Immutable Compliance │ │ Score (0-100) │ │ Timestamp Proof │ │ Threat Hash │ └──────────────────────┘

## Key Features

- **Real-time Verification**: Every compliance score is hash-verified and timestamped on-chain
- **Aerospace-Grade Security**: Designed for mission-critical systems requiring cryptographic proof
- **Insurance Integration**: Enables automated premium adjustments based on verified security posture
- **Federal Ready**: Aligns with CMMC 2.0 and NIST frameworks for government contractors

## Contract Interfaces

### GreyvaultRegistry
Manages verified client identities and access control
```solidity
function registerClient(address client, string calldata identifier) external
function verifyClient(address client) external view returns (bool)
function updateClientStatus(address client, uint8 status) external

### GreyvaultThreatTM
Stores threat intelligence hashes and metadata
function submitThreat(bytes32 threatHash, uint256 severity, uint256 category) external
function getThreatData(bytes32 threatHash) external view returns (ThreatData)
function getClientThreats(address client) external view returns (bytes32[])

### GreyvaultCompliance
Records immutable compliance scores with blockchain proof
function submitComplianceScore(address client, uint256 score, bytes32 verification) external
function getLatestScore(address client) external view returns (uint256, uint256, bytes32)
function getScoreHistory(address client) external view returns (ScoreRecord[])

### Verification
Independently verify any compliance score:
// Verify score on-chain
const score = await greyvaultCompliance.getLatestScore(clientAddress);
console.log(`Score: ${score[0]}, Block: ${score[1]}, Hash: ${score[2]}`);

### Integration
For API integration and real-time threat feeds, see trustcore-api.
For aerospace-specific implementation guides, see aerospace-compliance.

### Security Audits
Self-Audit: December 2025
Third-party audit: Pending Phase II funding

### License
Proprietary - Greyvault Intelligence, Inc. All rights reserved.

### Contact
Federal/Enterprise Partnerships: deonate@greyvaultintel.xyz
