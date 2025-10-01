feat: Implement delete report and PBIX report endpoints

- Add deleteReport function with proper error handling and success validation
- Refactor onDeleteClick to only open confirmation dialog without executing deletion
- Move deletion logic from onDeleteClick to deleteReport function for proper confirmation flow
- Fix API endpoint URL duplication issue (removed redundant /riskmonitoring/api prefix)
- Add response validation before showing success message to prevent false positives
- Improve error handling with user-friendly messages and proper logging
- Update grid to refresh after successful deletion using applyTransaction