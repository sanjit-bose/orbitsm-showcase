# Architecture Overview

OrbitSM is designed as an enterprise ITSM platform with a browser-based frontend, an API backend, a relational persistence layer, and an AI-assisted intelligence layer.

This document intentionally describes the architecture at a public-safe level. It does not expose source code, schema definitions, private configuration, AI prompts, or proprietary implementation details.

## High-Level Architecture

![Architecture](../diagrams/architecture.png)

## Frontend Technology Stack

The product uses a modern web frontend built around:

- Next.js application shell.
- React-based pages and components.
- Project-aware navigation and context selection.
- Dashboard, Kanban, admin, workflow, and record-detail views.
- Same-origin API access in hardened deployments.

## Backend Technology Stack

The backend is API-driven and designed for enterprise workflow services:

- Python service runtime.
- FastAPI API layer.
- Gunicorn/Uvicorn production worker model.
- Modular route surfaces for incidents, tasks, requests, problems, changes, projects, users, auth, admin, analytics, and knowledge.
- Server-side workflow and authorization enforcement.

## Database Architecture

The persistence model is relational and supports:

- Users, roles, project memberships, and customer/account context.
- Incidents, service requests, tasks, problems, and changes.
- SLA metadata, lifecycle states, assignments, comments, attachments, and audit events.
- Knowledge article and KEDB generation outputs.
- Admin-managed project and platform settings.

PostgreSQL is used as the system of record, with pooled database access for production workloads.

## AI Capabilities

OrbitSM includes an AI intelligence layer for:

- RCA assistance.
- Similar-incident discovery.
- Situation grouping.
- SLA risk signals.
- AI-generated KB/KEDB article drafts.
- Dashboard insights and operational recommendations.

The public showcase intentionally avoids exposing prompts, model orchestration details, proprietary scoring logic, and implementation code.

## Workflow Engine

The workflow model supports controlled lifecycle movement across:

- Incidents.
- Tasks.
- Service requests.
- Problems.
- Changes.

Workflow controls include state transitions, assignment, reassignment, project correction, comments, notifications, audit events, and SLA status.

![Workflow](../diagrams/workflow.png)

## Deployment Architecture

The recommended deployment model uses:

- Browser access over HTTPS.
- Nginx reverse proxy at the edge.
- Next.js frontend on a private service network.
- FastAPI backend on a private service network.
- PostgreSQL database on a private service network.
- Backend-only access to SMTP/OAuth and secret-bearing services.

![Deployment](../diagrams/deployment.png)

## Security Architecture

Security is handled through layered controls:

- Authentication for protected application views and APIs.
- RBAC and project/customer data scoping.
- Backend validation of workflow authority.
- Private backend/database network exposure.
- Backend-only secrets.
- HTTPS and security headers.
- Audit logging for administrative and workflow actions.

