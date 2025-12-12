# Changelog

All notable changes to the JobWiz Browser Extension will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [0.5.3] - 2025-12-12

### Fixed
- **Workday job-specific resume matching** - Fixed URL matching for Workday platforms (e.g., `myworkdayjobs.com`)
  - Added support for Workday's alphanumeric job IDs (e.g., `_R25556`, `_JOB12345`)
  - Optimized resumes now correctly match when visiting Workday job pages
- **Improved job ID extraction** - Added support for:
  - Workday: `_R25556` pattern at end of URL path
  - Ashby: `ashby_jid` query parameter
  - Better fallback for Greenhouse/Lever numeric IDs

---

## [0.5.2] - 2025-12-12

### Fixed
- **Complete removal of ALL debug logging from content scripts** - Removed remaining console.log/error/warn statements from `side-panel.tsx` and `job-page.ts` that were missed in v0.5.1
- Affected files: `side-panel.tsx` (~60 statements), `job-page.ts` (~15 statements)
- Production builds now have zero console output for professional appearance

---

## [0.5.1] - 2025-12-12

### Fixed
- **Removed debug logging from production build** - Cleaned up all verbose console.log statements from side-panel hooks that were appearing in browser console
- Affected hooks: `useLinkedInDetection`, `useMatchScore`, `useUrlWatcher`, `useResumes`, `useJobDetection`, `useAuth`, `useJobApplicationState`

---

## [0.5.0] - 2025-12-12

### Changed

**Side-Panel Architecture Refactoring**
- Refactored monolithic side-panel (2500+ lines) into modular components
- Extracted reusable hooks: `useAuth`, `useResumes`, `useJobDetection`, `useMatchScore`, `useLinkedInDetection`, `useJobApplicationState`, `useUrlWatcher`, `usePanelState`
- Created dedicated UI components: `CollapsedTab`, `PanelHeader`, `SettingsPanel`, `JobInfoCard`, `ResumeSelectorCard`, `MatchScoreDisplay`, `AppliedSuccessCard`, `AutofillButton`, `UploadResumeButton`, `LinkedInHintMessage`, `LoadingState`, `AuthenticationBarrier`, `NoJobDetected`, `NoResumesWarning`, `ErrorMessage`
- Added `SidePanelContext` for shared state management
- Improved code maintainability and testability

### Fixed
- Removed all console.log statements (ESLint compliance)
- Fixed ESLint errors and warnings across browser extension
- Improved error handling in side-panel components

### Added
- Added Firestore indexes for job application saves
- Added comprehensive type definitions for side-panel state

---

## [0.4.0] - 2025-12-11

### Added

**Major Platform Expansion**
- **Ashby ATS Support** - Detects jobs on Shopify, Notion, Ramp, OpenAI, and 2,700+ other companies using Ashby
  - Automatically detects `ashby_jid` parameter in URLs
  - Extracts job data from JSON-LD JobPosting schema
  - Full support for `jobs.ashbyhq.com` and embedded Ashby careers pages

- **Amazon Jobs Support** - Full detection for Amazon and AWS positions
  - Supports `amazon.jobs` and `www.amazon.jobs` domains
  - Handles Amazon's dynamic content loading
  - Extracts job title, location, description, and salary when available

- **Oracle Fusion HCM Support** - Detection for Oracle career pages
  - Supports `careers.oracle.com` and `*.oraclecloud.com` domains
  - Waits for Oracle's dynamic content to load before extraction

- **Eightfold AI Support** - Detection for Netflix and other Eightfold-powered sites
  - Supports `*.jobs.netflix.net` and `*.eightfold.ai` domains
  - Extracts from JSON-LD structured data embedded in pages

- **Generic Job Detector** - Fallback detection for custom career sites
  - Automatically detects pages with schema.org JobPosting markup
  - Supports Airbnb, Google, Apple, Microsoft, Meta career pages
  - DOM-based extraction fallback when JSON-LD not available

### Changed
- Expanded content script matches to include new platforms
- Added host permissions for all newly supported domains
- Reorganized detector registration order (specific detectors first, generic last)

### Supported Platforms (Total: 12+)
| Platform | Type | Companies |
|----------|------|-----------|
| LinkedIn | Job Board | LinkedIn Jobs |
| Indeed | Job Board | Indeed |
| Glassdoor | Job Board | Glassdoor |
| Dice | Job Board | Dice |
| Greenhouse | ATS | 1000s of companies |
| Lever | ATS | 1000s of companies |
| Workday | ATS | Enterprise companies |
| Eightfold | ATS | Netflix, etc. |
| Ashby | ATS | Shopify, Notion, Ramp, OpenAI, etc. |
| Amazon | Custom | Amazon, AWS |
| Oracle | Custom | Oracle |
| Generic | Fallback | Any site with JobPosting schema |

---

## [0.3.2] - 2025-12-10

### Fixed
- Browser extension v0.3.2 fixes for multi-provider AI integration

---

## [0.3.0] - 2025-11-15

### Added
- One-click autofill for job applications
- Automatic application tracking
- Support for LinkedIn, Indeed, Glassdoor, and major job boards
- Secure OAuth 2.0 PKCE authentication
- Smart resume selection
- Job detection on supported platforms
- Offline state management
- Cross-tab communication

### Features
- Plasmo framework-based architecture
- Modern popup UI with Tailwind CSS
- Background service worker for persistence
- Message protocol for extension-webapp communication
- Job data extraction and validation
- Resume readiness scoring

### Security
- CSRF protection on all endpoints
- XSS sanitization for user input
- Minimal Chrome permissions (storage, activeTab, scripting)
- Secure HTTPS communication with API
- JWT token-based authentication with refresh

---

**Note**: This is a private beta release for invited users only.
