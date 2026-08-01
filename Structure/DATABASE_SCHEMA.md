# DATABASE SCHEMA

Project:
AI Accessibility Production Platform

Version:
1.0

Database

SQLite (MVP)

SQL Server (Enterprise)

PostgreSQL (Future)

---

# Philosophy

Database stores project metadata.

PDF contents remain inside original files.

Never duplicate large binary content unnecessarily.

---

# Core Tables

Projects

Documents

Pages

OCRResults

AITasks

ValidationResults

AccessibilityNodes

Bookmarks

TOC

Metadata

Reports

Users

Licenses

Plugins

AuditLogs

Notifications

Settings

Workflows

Queues

Workers

Templates

Tags

Forms

Tables

AltTexts

History

CacheIndex

---

# Projects

ProjectId

Name

Description

CreatedDate

ModifiedDate

Owner

Status

HealthScore

---

# Documents

DocumentId

ProjectId

Name

OriginalPath

Hash

PageCount

Language

DocumentType

OCRStatus

ValidationStatus

CreatedDate

ModifiedDate

---

# Pages

PageId

DocumentId

PageNumber

Width

Height

Rotation

OCRCompleted

HealthScore

---

# OCR Results

OCRId

PageId

Provider

Language

Confidence

ExecutionTime

Cached

CreatedDate

---

# AI Tasks

TaskId

DocumentId

Module

Provider

PromptVersion

Confidence

Duration

Cost

Status

---

# Validation Results

ValidationId

DocumentId

RuleId

Severity

Category

Message

AutoFixAvailable

Resolved

---

# Accessibility Nodes

NodeId

DocumentId

ParentId

Type

Role

Properties

Order

---

# Reports

ReportId

DocumentId

Type

GeneratedDate

GeneratedBy

ExportPath

---

# Workflows

WorkflowId

Name

Version

ExecutionTime

AutomationRate

Template

---

# Queue

QueueId

WorkerType

Priority

Status

CreatedDate

StartedDate

CompletedDate

---

# Workers

WorkerId

Type

Status

CurrentJob

CPUUsage

MemoryUsage

---

# Audit Logs

AuditId

Timestamp

User

Action

Target

Duration

Success

---

# Settings

Global

Workspace

Project

Document

---

# Indexes

ProjectId

DocumentId

PageId

RuleId

Status

Priority

Hash

CreatedDate

---

# Backup Strategy

Automatic

Incremental

Manual

Cloud (Future)

---

# Recovery

Auto Recovery

Integrity Check

Rollback

Backup Restore
