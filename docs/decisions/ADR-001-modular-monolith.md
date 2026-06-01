# ADR-001: Modular Monolith over Microservices

**Date:** 2025-06-01  

## Context
BizPilot is being built as a portfolio project targeting small grocery 
shop management. The developer has prior experience with monolithic 
architecture and limited experience with microservices.

## Decision
Start with a modular monolith using Spring Boot. Each business domain 
(inventory, sales, purchasing, ledger, expenses) is a self-contained 
module with clear package boundaries and no cross-module direct calls 
— only through defined interfaces.

## Reasons
- Avoids distributed transaction complexity on day one
- Faster time to working software
- Module boundaries still enforce separation of concerns
- Can extract individual modules to services later if needed
- More honest architecture for a solo developer building v1

## Consequences
- Cannot scale modules independently (acceptable at this stage)
- Migration to microservices later requires extracting modules into 
  separate Spring Boot apps — the clean boundaries make this feasible

## Future
Revisit after v1 is stable. Candidate first extraction: 
the inventory module, since it has the most independent logic.