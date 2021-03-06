---
title: 'Vorgehensweise: Binden des DataGrid-Steuerelements in Windows Forms an eine Datenquelle mithilfe des Designers'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- datasets [Windows Forms], binding to DataGrid control
- data binding [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], data binding
- Windows Forms controls, data binding
- bound controls [Windows Forms]
ms.assetid: 4e96e3d0-b1cc-4de1-8774-bc9970ec4554
ms.openlocfilehash: 665a1af990aaf615c763c1c2eae508024d9de5c7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917827"
---
# <a name="how-to-bind-the-windows-forms-datagrid-control-to-a-data-source-using-the-designer"></a>Vorgehensweise: Binden des DataGrid-Steuerelements in Windows Forms an eine Datenquelle mithilfe des Designers

> [!NOTE]
> Obwohl das <xref:System.Windows.Forms.DataGridView>-Steuerelement das <xref:System.Windows.Forms.DataGrid>-Steuerelement ersetzt und funktionell erweitert, wird das <xref:System.Windows.Forms.DataGrid>-Steuerelement sowohl aus Gründen der Abwärtskompatibilität als auch, falls gewünscht, für die zukünftige Verwendung beibehalten. Weitere Informationen finden Sie unter [Unterschiede zwischen dem DataGridView-Steuerelement und dem DataGrid-Steuerelement in Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Das Windows Forms <xref:System.Windows.Forms.DataGrid> -Steuerelement wurde speziell zum Anzeigen von Informationen aus einer Datenquelle entwickelt. Sie binden das Steuerelement zur Entwurfszeit, indem <xref:System.Windows.Forms.DataGrid.DataSource%2A> Sie <xref:System.Windows.Forms.DataGrid.DataMember%2A> die-Eigenschaft und die-Eigenschaft festlegen oder <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A> zur Laufzeit durch Aufrufen der-Methode. Obwohl Sie Daten aus einer Vielzahl von Datenquellen anzeigen können, handelt es sich bei den meisten Quellen um Datasets und Datenansichten.

 Wenn die Datenquelle zur Entwurfszeit verfügbar ist – z. b. wenn das Formular eine Instanz eines Datasets oder einer Daten Sicht enthält – können Sie das Raster zur Entwurfszeit an die Datenquelle binden. Sie können dann eine Vorschau der Daten anzeigen, die im Raster angezeigt werden.

 Sie können das Raster zur Laufzeit auch Programm gesteuert binden. Dies ist hilfreich, wenn Sie eine Datenquelle basierend auf Informationen festlegen möchten, die Sie zur Laufzeit erhalten. Die Anwendung kann z. b. den Namen einer Tabelle angeben, die Sie anzeigen möchten. Dies ist auch in Situationen erforderlich, in denen die Datenquelle zur Entwurfszeit nicht vorhanden ist. Dies schließt Datenquellen ein, z. b. Arrays, Auflistungen, nicht typisierte Datasets und Daten Leser.

 Das folgende Verfahren erfordert ein **Windows-Anwendungs** Projekt mit einem Formular, <xref:System.Windows.Forms.DataGrid> das ein-Steuerelement enthält. Weitere Informationen zum Einrichten eines solchen Projekts finden [Sie unter Gewusst wie: Erstellen Sie ein Windows Forms-](/visualstudio/ide/step-1-create-a-windows-forms-application-project) Anwendungs [Projekt, und Gewusst wie: Fügen Sie Windows Forms](how-to-add-controls-to-windows-forms.md)Steuerelemente hinzu. In Visual Studio 2005 ist das <xref:System.Windows.Forms.DataGrid> Steuerelement standardmäßig nicht in der **Toolbox** . Weitere Informationen zum Hinzufügen finden [Sie unter Gewusst wie: Fügen Sie der Toolbox](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))Elemente hinzu. Darüber hinaus können Sie in Visual Studio 2005 das Fenster **Datenquellen** für die Datenbindung zur Entwurfszeit verwenden. Weitere Informationen finden Sie unterbinden von Steuer [Elementen an Daten in Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).

## <a name="to-data-bind-the-datagrid-control-to-a-single-table-in-the-designer"></a>So binden Sie das DataGrid-Steuerelement an eine einzelne Tabelle im Designer

1. Legen Sie die- <xref:System.Windows.Forms.DataGrid.DataSource%2A> Eigenschaft des Steuer Elements auf das-Objekt fest, das die Datenelemente enthält, an die Sie binden möchten

2. Wenn die Datenquelle ein DataSet ist, legen Sie <xref:System.Windows.Forms.DataGrid.DataMember%2A> die-Eigenschaft auf den Namen der Tabelle fest, an die die Bindung erfolgen soll.

3. Wenn es sich bei der Datenquelle um ein DataSet oder eine Datenansicht handelt, die auf einer Datasettabelle basiert, fügen Sie dem Formular Code hinzu, um das DataSet zu füllen.

     Der genaue Code, den Sie verwenden, hängt davon ab, wo das DataSet Daten erhält. Wenn das Dataset direkt aus einer Datenbank aufgefüllt wird, wird in der Regel die `Fill` -Methode eines Daten Adapters aufgerufen, wie im folgenden Codebeispiel gezeigt, das ein DataSet mit dem `DsCategories1`Namen auffüllt:

    ```vb
    sqlDataAdapter1.Fill(DsCategories1)
    ```

    ```csharp
    sqlDataAdapter1.Fill(DsCategories1);
    ```

    ```cpp
    sqlDataAdapter1->Fill(dsCategories1);
    ```

4. Optionale Fügen Sie dem Raster die entsprechenden Tabellen Stile und Spalten Stile hinzu.

     Wenn keine Tabellen Stile vorhanden sind, wird die Tabelle angezeigt, jedoch mit minimaler Formatierung und allen sichtbaren Spalten.

## <a name="to-data-bind-the-datagrid-control-to-multiple-tables-in-a-dataset-in-the-designer"></a>So binden Sie das DataGrid-Steuerelement an mehrere Tabellen in einem Dataset im Designer

1. Legen Sie die- <xref:System.Windows.Forms.DataGrid.DataSource%2A> Eigenschaft des Steuer Elements auf das-Objekt fest, das die Datenelemente enthält, an die Sie binden möchten

2. Wenn das Dataset verknüpfte Tabellen enthält (d. h., wenn es ein Beziehungs Objekt enthält) <xref:System.Windows.Forms.DataGrid.DataMember%2A> , legen Sie die-Eigenschaft auf den Namen der übergeordneten Tabelle fest.

3. Schreiben Sie Code, um das DataSet auszufüllen.

## <a name="see-also"></a>Siehe auch

- [Übersicht über das DataGrid-Steuerelement](datagrid-control-overview-windows-forms.md)
- [Vorgehensweise: Hinzufügen von Tabellen und Spalten zum Windows Forms DataGrid-Steuerelement](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [DataGrid-Steuerelement](datagrid-control-windows-forms.md)
- [Windows Forms-Datenbindung](../windows-forms-data-binding.md)
- [Zugreifen auf Daten in Visual Studio](/visualstudio/data-tools/accessing-data-in-visual-studio)
