---
title: 'Vorgehensweise: Bereitstellen von Hilfe in einer Windows-Anwendung'
ms.date: 03/30/2017
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
ms.openlocfilehash: 2f9c0a9791db28cebd055ca446fdff16b9e276a4
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959613"
---
# <a name="how-to-provide-help-in-a-windows-application"></a>Vorgehensweise: Bereitstellen von Hilfe in einer Windows-Anwendung

Möglich nutzen die <xref:System.Windows.Forms.HelpProvider> Komponente, um Hilfethemen in einer Hilfedatei bestimmten Steuerelementen in Windows Forms zuzuordnen. Die Hilfedatei kann entweder im Format HTML oder HTMLHelp 1.x oder höher vorliegen.

## <a name="provide-help"></a>Bereitstellen von Hilfe

1. In Visual Studio aus der **Toolbox**, ziehen Sie eine <xref:System.Windows.Forms.HelpProvider> Ihrem Formular.

     Die Komponente befindet sich anschließend auf der Taskleiste unten im Windows Forms-Designer.

2. In der **Eigenschaften** legen die <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> -Eigenschaft auf die CHM-, col- oder htm-Hilfedatei.

3. Wählen Sie ein anderes Steuerelement, die Sie in das Formular, und in der **Eigenschaften** legen die <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> Eigenschaft.

     Dies ist die Zeichenfolge, die durch Übergeben der <xref:System.Windows.Forms.HelpProvider> Komponente, an der Hilfe-Datei in das entsprechende Hilfethema aufzurufen.

4. In der **Eigenschaften** legen die <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> Eigenschaft mit einem Wert, der die <xref:System.Windows.Forms.HelpNavigator> Enumeration.

     Dies bestimmt die Art, wie die **HelpKeyword**-Eigenschaft an das Hilfesystem übergeben wird. In der folgenden Tabelle werden die möglichen Einstellungen und ihre Beschreibungen aufgeführt.

    |Membername|Beschreibung|
    |-----------------|-----------------|
    |AssociateIndex|Gibt an, dass der Index für ein Thema in der angegebenen URL ausgeführt wurde.|
    |Find|Gibt an, dass die Suchseite der angegebenen URL angezeigt wird.|
    |Index|Gibt an, dass der Index der angegebenen URL angezeigt wird.|
    |KeywordIndex|Gibt ein Schlüsselwort an, nach dem gesucht wird, und die Aktion, die in der angegebenen URL vorzunehmen ist.|
    |TableOfContents|Gibt an, dass das Inhaltsverzeichnis der HTML 1.0-Hilfedatei angezeigt wird.|
    |Topic|Gibt an, dass das Thema angezeigt wird, auf das durch die angegebene URL verwiesen wird.|

 Zur Laufzeit durch Drücken von F1 bei der das Steuerelement, für die Sie festgelegt haben die **HelpKeyword** und **HelpNavigator** Eigenschaften – hat Fokus öffnet die Hilfedatei, die Sie zugeordnet sind, <xref:System.Windows.Forms.HelpProvider> Komponente.

 Derzeit den **HelpNamespace** unterstützt-Eigenschaft Hilfedateien in den folgenden drei Formaten: HTMLHelp 1.x, HTMLHelp 2.0 und HTML. Dies bedeutet, dass Sie die **HelpNamespace**-Eigenschaft auf eine http:// adresse (z. B. eine Webseite) festlegen können. Daraufhin wird im Standardbrowser die Webseite mit der Zeichenfolge geöffnet, die in der als Anker verwendeten **HelpKeyword**-Eigenschaft angegeben ist. Der Anker wird verwendet, um zu einem bestimmten Teil einer HTML-Seite zu springen.

> [!IMPORTANT]
> Überprüfen Sie alle von einem Client gesendeten Informationen sorgfältig, bevor Sie diese in der Anwendung verwenden. Böswillige Benutzer könnten versuchen, ausführbare Skripts, SQL-Anweisungen oder anderen Code zu senden oder einzuschleusen. Bevor Sie die Eingabe eines Benutzers anzeigen, diese in einer Datenbank speichern oder damit arbeiten, müssen Sie sicherstellen, dass diese keine potenziell unsicheren Informationen enthält. Ein sehr gebräuchlicher Weg zur Überprüfung der von einem Benutzer übermittelten Eingaben ist die Verwendung eines regulären Ausdrucks, um nach Schlüsselwörtern wie SCRIPT zu suchen.

Sie können auch die <xref:System.Windows.Forms.HelpProvider> Komponente zum Anzeigen der kontextbezogenen Hilfe, selbst wenn Sie so konfiguriert, dass die Hilfedateien für die auf Windows Forms-Steuerelemente anzuzeigen. Weitere Informationen finden Sie unter [Vorgehensweise: Anzeigen der kontextbezogenen Hilfe](how-to-display-pop-up-help.md).

## <a name="see-also"></a>Siehe auch

- [Vorgehensweise: Anzeigen der kontextbezogenen Hilfe](how-to-display-pop-up-help.md)
- [Benutzerführung mithilfe von QuickInfos](control-help-using-tooltips.md)
- [Integrieren von Benutzerhilfe in Windows Forms](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
