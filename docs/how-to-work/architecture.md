# Architecture

> **Document Type**: State (keep current)
> 
> Last updated: YYYY-MM-DD

---

## Overview

*One paragraph describing what this system does and its primary architectural style (monolith, microservices, serverless, etc.)*

---

## System Diagram

```
┌─────────────┐     ┌─────────────┐     ┌─────────────┐
│             │     │             │     │             │
│   Client    │────▶│   Server    │────▶│  Database   │
│             │     │             │     │             │
└─────────────┘     └─────────────┘     └─────────────┘
```

*Replace with actual architecture diagram*

---

## Components

### Component Name

**Responsibility**: *What this component does*

**Location**: `src/path/to/component`

**Key interfaces**:
- *Interface or API it exposes*

**Dependencies**:
- *What it depends on*

---

## Data Flow

*Describe how data moves through the system for key operations*

### Example Flow: User Action

1. Client sends request to...
2. Server validates...
3. Database stores...
4. Response returns...

---

## Key Patterns

*Document patterns used consistently across the codebase*

### Pattern Name

**Where used**: *Components or areas*

**How it works**: *Brief explanation*

---

## Boundaries & Constraints

*Important limitations or boundaries in the architecture*

- *e.g., All external API calls go through the gateway service*
- *e.g., Database is never accessed directly from controllers*
