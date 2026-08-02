# PDF STRUCTURE ENGINE

Project:
AI Accessibility Production Platform (AAPP)

Version:
1.0

Status:
Core Architecture Specification

Priority:
Critical

---

# Purpose

The PDF Structure Engine is the most critical subsystem in the platform.

Unlike rendering engines, this engine is responsible for reading,
understanding, modifying, validating and writing Tagged PDF structures
without corrupting the document.

The engine must preserve accessibility, visual appearance, document integrity,
and optimize file size.

This subsystem is considered the technological foundation of the platform.

---

# Objectives

• Read existing Tagged PDFs.

• Read untagged PDFs.

• Analyze document objects.

• Build an internal object model.

• Modify accessibility structures.

• Write updated structure trees.

• Preserve object references.

• Prevent unnecessary object duplication.

• Minimize output file size.

• Support incremental save.

• Support full rebuild when required.

---

# Responsibilities

The engine owns every operation involving PDF structure.

It is NOT responsible for OCR.

It is NOT responsible for AI.

It is NOT responsible for accessibility decisions.

Those responsibilities belong to other modules.

The Structure Engine only provides accurate reading and writing capabilities.

---

# Supported Standards

PDF 1.7

ISO 32000

PDF 2.0 (Future)

PDF/UA

PDF/A (Read Support)

Section 508 Compatibility

WCAG Mapping Support

---

# Core Philosophy

The PDF file is treated as a structured graph,
not a sequence of pages.

Every object relationship must remain valid after editing.

---

# Internal Object Model

Every PDF is converted into an internal model before modifications begin.

Hierarchy

PdfDocument

↓

PdfPage

↓

StructureTree

↓

AccessibilityNode

↓

ParagraphNode

↓

HeadingNode

↓

ListNode

↓

TableNode

↓

FigureNode

↓

ArtifactNode

↓

FormNode

↓

AnnotationNode

---

# Internal Object Properties

Every node contains

Unique ID

Parent

Children

Role

Bounding Box

MCID

Page Reference

Object Reference

Attributes

Language

Alt Text

Actual Text

Metadata

Validation State

Dirty Flag

Confidence Score

---

# Reading Pipeline

Open PDF

↓

Read Header

↓

Read Cross Reference Table

↓

Read Trailer

↓

Load Objects

↓

Read Catalog

↓

Read Pages

↓

Read StructTreeRoot

↓

Read ParentTree

↓

Read RoleMap

↓

Read MCIDs

↓

Create Internal Model

↓

Validate Relationships

↓

Ready

---

# Writing Pipeline

Internal Model

↓

Detect Modified Nodes

↓

Validate Structure

↓

Optimize Objects

↓

Rebuild ParentTree

↓

Update MCIDs

↓

Update Cross References

↓

Optimize Object Streams

↓

Incremental Save

↓

Output PDF

---

# Incremental Save Strategy

Default behavior

Only modified objects are rewritten.

Unchanged objects remain untouched.

Benefits

Fast

Small file size

Lower memory usage

Enterprise friendly

---

# Full Save Strategy

Used only when

Structure corruption exists

Object references are invalid

Version upgrade required

Major optimization requested

---

# File Size Optimization

The engine must avoid:

Duplicate fonts

Duplicate images

Duplicate objects

Duplicate metadata

Duplicate streams

Unused resources

Unused references

Object fragmentation

Compression loss

---

# Object Cache

Frequently accessed objects remain in memory.

Unused objects are released.

Support lazy loading.

Support cache invalidation.

---

# Cross Reference Manager

Responsible for

Object numbering

Reference integrity

Incremental updates

Offset calculation

Free object management

---

# Structure Tree Manager

Responsible for

StructTreeRoot

ParentTree

RoleMap

ClassMap

IDTree

Node hierarchy

MCID mapping

Reading order integrity

---

# Object Manager

Creates

Reads

Updates

Deletes

Optimizes

References

Every PDF object.

---

# Validation

Before export

Check missing parents

Check orphan nodes

Check duplicate MCIDs

Check invalid references

Check circular hierarchy

Check role mapping

Check language metadata

Check object integrity

---

# Recovery Strategy

If corruption is detected

Attempt automatic repair.

If impossible

Rollback.

Generate detailed diagnostics.

Never export corrupted PDFs.

---

# Performance Requirements

Open large PDFs efficiently.

Support thousands of pages.

Process only modified objects.

Avoid full memory loading.

Support background processing.

---

# Threading Model

Reader

Writer

Optimizer

Validator

operate independently where possible.

UI thread must never be blocked.

---

# Error Handling

Every operation returns

Status

Warnings

Errors

Diagnostics

Recovery suggestions

Execution time

---

# Logging

Log

Object modifications

Structure rebuilds

Validation failures

Optimization statistics

Incremental saves

Recovery actions

---

# Security

Reject malformed PDFs.

Protect against object recursion attacks.

Limit memory usage.

Validate object boundaries.

Prevent malformed stream execution.

---

# Integration

The engine communicates with

OCR Engine

Validation Engine

Tagging Engine

Reading Order Engine

Forms Engine

Table Engine

Alt Text Engine

AI Orchestrator

Workflow Engine

Export Engine

---

# Future Capabilities

Incremental Structure Repair

Hybrid Save Engine

Streaming PDF Processing

Distributed Processing

GPU-assisted Parsing

Encrypted PDF Support

Digital Signature Preservation

Linearized PDF Optimization

Collaborative Editing

Real-time Validation

---

# Build vs Buy Evaluation

Before implementing a custom writer,
an engineering spike must evaluate existing technologies.

Evaluation Criteria

- Tagged PDF write support
- StructTree editing
- Incremental save
- Performance
- File size preservation
- PDF/UA compliance
- Licensing model
- Commercial restrictions
- Long-term maintainability
- Community activity
- API quality

Candidate Technologies

- PDFium
- PDFPig
- MuPDF
- PDFix SDK
- Apryse SDK
- iText 8
- Commercial PDF SDKs
- Hybrid Architecture (Recommended for evaluation)

No final implementation decision shall be made until the evaluation is complete.

---

# Success Criteria

The PDF Structure Engine is considered production-ready only if it can:

✓ Open enterprise-scale PDFs.

✓ Preserve document integrity.

✓ Modify accessibility structures safely.

✓ Maintain valid object references.

✓ Preserve or reduce output file size.

✓ Support incremental save.

✓ Pass PDF/UA validation.

✓ Pass PAC validation.

✓ Remain extensible for future document formats.
