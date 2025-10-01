async function deleteReport() {
  try {
    setIsOpen(false);
    const deletedRow = getSelectedRowData();
    
    if (deletedRow && deletedRow.length > 0) {
      const reportId = deletedRow[0]?.reportKey;
      
      if (reportId) {
        // Delete PBIX Report
        await riskMonitoringService.deletePbixReport(reportId);
        
        // Apply transaction to remove from grid
        gridRef.current.api.applyTransaction({ remove: deletedRow });
        
        // Show success message only after successful deletion
        rootContext.showSuccess('Report deleted successfully');
      }
    } else {
      rootContext.showInfo('Please select a report to delete.');
    }
  } catch (err: any) {
    const errMessage = 'Error deleting the report.';
    rootContext.showError(errMessage);
    logger.error('MARVEL DATA HUB', currentComponentName, err, errMessage);
  }
}