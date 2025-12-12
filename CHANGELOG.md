# Changelog

All notable changes to the JobWiz Browser Extension will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
- **Amazon Jobs Support** - Full detection for Amazon and AWS positions
- **Oracle Fusion HCM Support** - Detection for Oracle career pages
- **Eightfold AI Support** - Detection for Netflix and other Eightfold-powered sites
- **Generic Job Detector** - Fallback detection for custom career sites with schema.org JobPosting markup

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

## [0.3.0] - 2025-11-15

### Added
- One-click autofill for job applications
- Automatic application tracking
- Support for LinkedIn, Indeed, Glassdoor, and major job boards
- Secure OAuth 2.0 PKCE authentication
- Smart resume selection
- Job detection on supported platforms

### Security
- CSRF protection on all endpoints
- XSS sanitization for user input
- Minimal Chrome permissions (storage, activeTab, scripting)
- Secure HTTPS communication with API
- JWT token-based authentication with refresh

---

**Note**: This is a private beta release for invited users only.
