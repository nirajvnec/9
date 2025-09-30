Branch Name:
feature/implement-delete-report-endpoints
Commit Message:
feat: Implement delete report and PBIX report endpoints

- Implemented deletePbixReport method in PgRiskMonitoringService for deleting PBIX reports via DELETE API call to /riskmonitoring/api/PbiReport/DeletePBIXReport
- Implemented deleteReport method in PgRiskMonitoringService for deleting regular reports via DELETE API call to /riskmonitoring/api/RiskReport/DeleteReport
- Added riskMonitoringService dependency to ReportSharedComponent to enable delete report functionality
- Integrated deletePbixReport API call in ManagePBIReport onDeleteClick handler with error handling and grid refresh
- Integrated deleteReport API call in ReportSharedComponent onDeleteClick handler with error handling and success notifications
- Both methods accept reportKey parameter and include proper error logging

Related: RBW-712118