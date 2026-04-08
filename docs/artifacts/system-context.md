# System Context

**Type:** C4 Context
**Exported:** 2026-04-08T00:14:17.664Z
**Source:** PlanVersion

## Linked Requirements

- 35e02254-3bf0-421c-8e1c-56d03a515b36
- 9d2f5d45-a575-4828-8d25-5230c2ad8016
- 6dee6944-3cb6-41ce-89f7-99f84322c0d2
- 26ac31c6-4ddf-4d92-aa2d-bfd8dcd7832e
- 9c12d72f-ed31-464b-ad4b-d12554ecc45e
- 47129ebc-89ff-4e26-8e6e-57378789dd13
- 8520e9d8-b367-49c2-bb89-9e3ac6da844e
- d3f9b19d-5808-45dc-af8a-cf989e333f01

## Diagram

```mermaid
C4Context
  UpdateLayoutConfig($c4ShapeInRow="2", $c4BoundaryInRow="1")
  Person(user, "End User", "Uses web app, Registers and logs in - Trace FR-001 FR-002 UC-001")
  Person(admin, "Admin", "Manages challenges and competitions, Easy challenge UI - Trace FR-009 FR-011 NFR-002")
  Person(participant, "Participant", "Joins competitions, Views live scores - Trace FR-003 FR-004")

  System_Boundary(boundary, "Competition Platform") {
    System(platform, "Competition Platform", "Registration and login<br/>Live scoreboard via realtime stream<br/>Supports multiple game types - Trace FR-001 FR-002 FR-004 FR-005")
  }

  Rel(user, platform, "Registers", "HTTPS")
  Rel(user, platform, "Logs in", "HTTPS")
  Rel(admin, platform, "Manages competition", "HTTPS")
  Rel(participant, platform, "Joins competition", "WebSocket")
  Rel(platform, participant, "Streams scoreboard", "WebSocket")

  UpdateRelStyle(user, platform, $offsetY="-10")
  UpdateRelStyle(admin, platform, $offsetY="10")
  UpdateRelStyle(platform, participant, $offsetX="20")
```
