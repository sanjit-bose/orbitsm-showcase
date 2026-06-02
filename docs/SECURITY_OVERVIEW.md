# Security Overview

OrbitSM is designed with enterprise ITSM data protection and governance in mind.

This public showcase describes the security model at a high level. It does not expose implementation internals, source code, configuration, secrets, or private security logic.

## Authentication

Protected application views and APIs require authenticated access. The platform supports administrative onboarding and password-management flows.

## Authorization

Authorization is based on:

- Role.
- Project membership.
- Customer/account context.
- Management hierarchy.
- Work-item ownership or requester relationship.
- Admin privileges.

## Project and Customer Scoping

Employees can be restricted to assigned projects. Customers can be restricted to their own organization/account scope. Users may still see records they raised, even if broader project visibility is limited, depending on policy.

## Workflow Security

Workflow actions are expected to be validated server-side. Client-side buttons and screens are user experience controls, not security boundaries.

Examples of guarded workflow actions:

- Assign.
- Reassign.
- Change project.
- Transition status.
- Approve change.
- Close record.
- Add comment.
- Upload attachment.

## Secrets Boundary

Secrets belong only in backend/server-side configuration:

- Database credentials.
- JWT/signing material.
- SMTP credentials.
- OAuth client secrets.
- AI service credentials.

No browser-visible variable should contain a private secret.

## Deployment Security

The hardened deployment pattern includes:

- HTTPS edge.
- Security headers.
- Private backend/database network.
- Backend-only provider access.
- Public exposure limited to web entry points.

## Audit and Compliance

The platform is designed to support audit events for:

- User/account administration.
- Project and RBAC updates.
- Workflow transitions.
- Assignment/reassignment.
- Comments and notifications.
- Import and configuration actions.

