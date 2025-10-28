# How-to-display-each-row-as-a-single-record-in-Flutter-DataTable-SfDataGrid

In this article, we will show how to display each row as a single record in in [Flutter DataTable](https://www.syncfusion.com/flutter-widgets/flutter-datagrid).

Initialize the [SfDataGrid](https://pub.dev/documentation/syncfusion_flutter_datagrid/latest/datagrid/SfDataGrid-class.html) widget with the necessary properties. To display employee details and enable navigation, a modal bottom sheet is presented using the [showModalBottomSheet](https://api.flutter.dev/flutter/material/showModalBottomSheet.html) function, with its `isScrollControlled` property set to `true` for responsive content handling.

Inside the bottom sheet, a [StatefulBuilder](https://api.flutter.dev/flutter/widgets/StatefulBuilder-class.html) is used to manage `currentIndex`, ensuring that `employees[currentIndex]` is displayed dynamically. A custom helper `(keyValueRow)` is used to align labels and values by combining a fixed-width 
[SizedBox](https://api.flutter.dev/flutter/widgets/SizedBox-class.html) with an [Expanded](https://api.flutter.dev/flutter/widgets/Expanded-class.html) widget.  

The layout includes a header showing the record position, rows for ID, Name, Designation, and Salary, along with Previous and Next buttons that update currentIndex via setState. Each field uses keyValueRow for a clean, structured UI.


```dart
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(title: const Text('Syncfusion Flutter DataGrid')),
      body: Column(
        children: [
          Padding(
            padding: EdgeInsets.all(8.0),
            child: Align(
              alignment: Alignment.centerLeft,
              child: ElevatedButton(
                onPressed: () => _openRecordViewer(startIndex: 0), // This method is expected to show a modal bottom sheet
                child: Text('Open Record Viewer'),
              ),
            ),
          ),
          Expanded(
            child: SfDataGrid(
              source: employeeDataSource,
              columnWidthMode: ColumnWidthMode.fill,
              columns: <GridColumn>[
                GridColumn(
                  columnName: 'id',
                  label: Container(
                    padding: EdgeInsets.all(16.0),
                    alignment: Alignment.center,
                    child: Text('ID'),
                  ),
                ),
                GridColumn(
                  columnName: 'name',
                  label: Container(
                    padding: EdgeInsets.all(8.0),
                    alignment: Alignment.center,
                    child: Text('Name'),
                  ),
                ),
                GridColumn(
                  columnName: 'designation',
                  label: Container(
                    padding: EdgeInsets.all(8.0),
                    alignment: Alignment.center,
                    child: Text('Designation', overflow: TextOverflow.ellipsis),
                  ),
                ),
                GridColumn(
                  columnName: 'salary',
                  label: Container(
                    padding: EdgeInsets.all(8.0),
                    alignment: Alignment.center,
                    child: Text('Salary'),
                  ),
                ),
              ],
            ),
          ),
        ],
      ),
    );
  }

```

You can download this example on [GitHub](https://github.com/SyncfusionExamples/How-to-display-each-row-as-a-single-record-in-Flutter-DataTable-SfDataGrid).

