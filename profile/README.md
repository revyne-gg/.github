# Revyne

Open-core tournament management for esports.

Revyne is a self-hostable platform for organising, running, and scaling competitive gaming tournaments. It is built for tournament organisers, community leagues, and esports organisations that want serious infrastructure without starting from zero.

## What it does

Revyne handles the full lifecycle of a tournament: registration, bracket and match management, scheduling, results, and prize pools. Organisers get a modern web experience, players get a React Native mobile app, and developers get an SDK and stable contracts to build on top of.

## Architecture

Revyne is built as a distributed system from day one:

- Domain-specific .NET microservices, each owning its own PostgreSQL database
  - Every service comes with a ready to use Dockerfile and prebuilt images
- NATS for asynchronous messaging between services
- Envoy Gateway at the edge
- Ory stack (Kratos, Oathkeeper, Keto) for identity, authentication, and fine-grained authorisation
- React Native mobile client

## Open core

The open-source side of Revyne includes:

- The frontend
- Commodity backend services
- The SDK
- Proto and client contracts

Self-hosted builds support third-party tournament engine plugins, loaded at runtime via `AssemblyLoadContext`, so you can implement your own formats and rule sets behind the `ITournamentEngine` interface.

The hosted multi-tenant deployment, the first-party tournament engine, billing, and enterprise features remain closed source. The public OSS image stays clean: proprietary components are layered in downstream and never touch the open repository.

## Status

Revyne is under active development. Contributions, feedback, and bug reports are welcome.

## Licence

See LICENSE for details on the open-source components.
