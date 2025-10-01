const onDeleteClick = async () => {
  const deletedRow = getSelectedRowData();

  if (deletedRow && deletedRow.length > 0) {
    setReportName(deletedRow[0]?.reportName);
    setIsOpen(true);

    try {
      const reportId = deletedRow[0]?.reportKey;

      if (reportId) {
        // Delete PBIX Report
        const response = await riskMonitoringService.deletePbixReport(reportId);

        // Check if deletion was successful
        if (response && response.success) {
          // Show success message
          rootContext.showInfo('Report deleted successfully.');

          // Reload reports to refresh the grid
          await loadReports();
        } else {
          // Show error if response indicates failure
          const errorMessage = response?.message || 'Failed to delete report.';
          rootContext.showError(`${errorMessage} Please try again.`);
          console.error('Delete failed', response);
        }
      }
    } catch (err: any) {
      // Handle error
      const errMessage = 'Error deleting report!';
      rootContext.showError(`${errMessage} Please try again sometime.`);
      console.error('Delete error!', err);
    }
  } else {
    rootContext.showInfo('Please select a report to delete.');
  }
};