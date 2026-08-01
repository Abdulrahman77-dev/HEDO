# CODING STANDARDS

Project:
AI Accessibility Production Platform (AAPP)

Version:
1.0

Status:
Development Guidelines

---

# Philosophy

The project must be maintainable for at least 10 years.

Code readability is more important than clever code.

Every module must be testable.

Every service must be replaceable.

SOLID principles are mandatory.

Clean Architecture is mandatory.

---

# Technology Stack

Framework:
.NET 9

Language:
C# 13

UI:
WPF

Pattern:
MVVM

Dependency Injection:
Microsoft.Extensions.DependencyInjection

Logging:
Serilog

Database:
SQLite (MVP)
SQL Server (Enterprise)

ORM:
Entity Framework Core

Testing:
xUnit

Mocking:
Moq

PDF Processing:
PDFium + PDFPig + Custom Engine

AI Providers:
OpenAI
Anthropic
Azure OpenAI
Local Models (Future)

OCR Providers

Tesseract

Windows OCR

ABBYY (Plugin)

Azure OCR (Plugin)

---

# Project Structure

src/

Core/

Application/

Infrastructure/

Presentation/

Shared/

Plugins/

Tests/

Docs/

Assets/

---

# Naming Conventions

Namespaces

Company.Product.Module

Example

AAPP.Core

AAPP.Application

AAPP.Infrastructure

---

Classes

PascalCase

Example

DocumentAnalyzer

OCRService

HealthEngine

---

Interfaces

Prefix with I

IDocumentService

IOCRProvider

IAIProvider

IExportEngine

---

Private Fields

_prefixCamelCase

Example

_logger

_cache

_database

---

Properties

PascalCase

DocumentName

HealthScore

PageCount

---

Methods

PascalCase

AnalyzeDocument()

RunOCR()

GenerateAltText()

ExportPDF()

---

Variables

camelCase

pageNumber

healthScore

validationResult

---

Constants

PascalCase

MaximumPages

DefaultLanguage

SupportedFormats

---

Async Methods

Must end with Async

LoadProjectAsync()

RunOCRAsync()

ExportAsync()

---

# Folder Organization

One Class Per File

One Public Type Per File

Related files grouped into folders

No God Classes

---

# Maximum File Size

Recommended

< 400 Lines

Hard Limit

800 Lines

Split into smaller classes whenever possible.

---

# Dependency Rules

Presentation

↓

Application

↓

Domain

↓

Infrastructure

Never reverse dependencies.

---

# Dependency Injection

Never instantiate services manually.

Use Constructor Injection only.

Avoid Service Locator Pattern.

---

# Error Handling

Never swallow exceptions.

Always log unexpected exceptions.

Provide meaningful error messages.

Use custom exception types when appropriate.

---

# Logging

Use Structured Logging.

Log Levels

Trace

Debug

Information

Warning

Error

Critical

Never log sensitive customer data.

---

# Validation

Validate all public inputs.

Fail fast.

Return meaningful validation results.

---

# Nullability

Nullable Reference Types enabled.

Never suppress warnings without justification.

---

# Asynchronous Programming

Prefer async/await.

Avoid blocking calls.

Avoid async void except UI events.

Support CancellationToken.

---

# Performance

Lazy Loading

Streaming

Memory Pooling

Object Reuse

Parallel Processing when safe

Avoid unnecessary allocations

---

# Thread Safety

Background workers must be thread-safe.

Avoid shared mutable state.

Use Concurrent Collections where necessary.

---

# Configuration

Store in JSON.

Support environment overrides.

Never hardcode secrets.

---

# Security

Encrypt sensitive configuration.

Validate plugin signatures.

Sanitize file paths.

Protect temporary files.

Support offline enterprise mode.

---

# Unit Testing

Minimum Coverage

80%

Critical Engines

90%+

Test Types

Unit Tests

Integration Tests

Performance Tests

Regression Tests

---

# Git Strategy

Main

Development

Feature/*

Hotfix/*

Release/*

---

# Commit Convention

feat:

fix:

refactor:

test:

docs:

perf:

style:

build:

ci:

Example

feat(ocr): add parallel OCR pipeline

fix(tags): preserve heading hierarchy

refactor(ai): split provider abstraction

---

# Pull Request Rules

At least one reviewer.

All tests pass.

No compiler warnings.

Documentation updated.

---

# Code Review Checklist

Readable

Tested

Documented

No duplicated code

No dead code

Proper exception handling

Performance considered

Security considered

Accessibility considered

---

# Documentation

Every public class must contain XML Documentation.

Complex algorithms require architecture notes.

README updated when introducing major features.

---

# Design Principles

SOLID

DRY

KISS

YAGNI

Composition over Inheritance

Dependency Inversion

---

# Future-Proofing

Avoid vendor lock-in.

Abstract external providers.

Keep modules independent.

Prefer interfaces over implementations.

Design for extensibility.

---

# Definition of Done

✔ Code Compiles

✔ Unit Tests Pass

✔ No Warnings

✔ Documentation Updated

✔ Reviewed

✔ Feature Demonstrated

✔ Performance Verified

✔ Accessibility Rules Respected

✔ Ready for Release
