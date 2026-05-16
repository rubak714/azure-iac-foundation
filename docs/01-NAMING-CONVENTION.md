# Naming convention - Hessler Logistik GmbH

Every Azure resource follows a predictable name so the team can find things six months from now without guessing. This document is the source of truth. If a resource does not match the pattern, it gets renamed or rebuilt.

## Pattern

`<resource-type>-<workload>-<environment>-<region>-<instance>`

| Token | Allowed values | Example |
| --- | --- | --- |
| resource-type | `rg`, `vnet`, `snet`, `vm`, `kv`, `log`, `nsg`, `pip`, `nic` | `rg` |
| workload | `shared`, `freight`, `web`, `identity` | `shared` |
| environment | `dev`, `test`, `prod`, `sandbox` | `prod` |
| region | `gwc` (Germany West Central), `gn` (Germany North) | `gwc` |
| instance | `001`, `002`, ... | `001` |

## Worked examples

| Resource | Name |
| --- | --- |
| Resource group for shared services in prod | `rg-shared-prod-gwc-001` |
| Log Analytics workspace for the shared RG | `log-shared-prod-gwc-001` |
| Key Vault for shared secrets | `kv-shared-prod-gwc-001` |
| Future production virtual network for freight | `vnet-freight-prod-gwc-001` |
| Future production VM hosting the freight portal | `vm-freight-prod-gwc-001` |

## Exceptions

Some Azure services have stricter name rules. These are documented exceptions to the pattern:

### Storage accounts

Globally unique, all lowercase, no hyphens, 3-24 characters.
Pattern: `st<workload><env>gwc<random4>`.
Example: `stshareddevgwc7a2b`.

### Key Vaults

Globally unique. We use the standard pattern but accept that the name might
collide; if it does, add a 3-digit random suffix.
Example fallback: `kv-shared-prod-gwc-001-742`.

## Why a naming convention matters

Without one, a six-month-old subscription contains forty resources named `mystuff`, `test1`, `temp-rg`, `kkk-final-v2`. Nobody knows what is safe to delete. The bill becomes opaque. Auditors lose patience.

Industry data from Microsoft's own Cloud Adoption Framework documents this as the number-one cause of cloud sprawl in small and medium businesses.

## Enforcement

Two mechanisms enforce the convention:

1. **Bicep parameters** require the tokens, so a deployment cannot create a resource with a malformed name.
2. **Azure Policy** (added in module 4) will warn on resources created outside Bicep that do not match the pattern.

## Mandatory tags

Every resource also carries these tags:

| Tag | Example | Purpose |
| --- | --- | --- |
| `CostCenter` | `IT-001`, `FREIGHT-002` | Finance chargeback |
| `Environment` | `Production`, `Development` | Lifecycle automation |
| `Workload` | `Shared`, `Freight` | Cross-RG grouping |
| `Owner` | `cloud-team@hessler-logistik.de` | Incident routing |
| `ManagedBy` | `Bicep`, `Manual` | Who is allowed to change this |
| `CreatedDate` | `2026-05-16` | Audit trail |

The `CostCenter` tag is the most important. Without it, finance cannot break down the cloud bill by department, which is the first thing they ask for.