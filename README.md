const onDeleteClick = async () => {
  const deletedRow = getSelectedRowData();

  if (deletedRow && deletedRow.length > 0) {
    setReportName(deletedRow[0]?.reportName);
    setIsOpen(true);
  } else {
    rootContext.showInfo('Please select a report to delete.');
  }
};