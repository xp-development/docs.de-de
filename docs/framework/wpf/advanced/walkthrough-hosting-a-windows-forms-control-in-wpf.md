---
title: 'Exemplarische Vorgehensweise: Hosten eines Windows Forms-Steuerelements in WPF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hosting Windows Forms control in WPF [WPF]
ms.assetid: 9cb88415-39b0-4c46-80c4-ff325b674286
ms.openlocfilehash: e353c35e9989e5887e038371672adbb6c2d3598d
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976529"
---
# <a name="walkthrough-hosting-a-windows-forms-control-in-wpf"></a>Exemplarische Vorgehensweise: Hosten eines Windows Forms-Steuerelements in WPF

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stellt viele Steuerelemente mit einem großen Funktionsumfang bereit. Es kann jedoch vorkommen, dass Sie [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-Steuerelemente auf Ihren [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Seiten verwenden möchten. Beispielsweise haben Sie möglicherweise beträchtliche Investitionen in vorhandene [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-Steuerelemente, oder Sie verfügen über ein [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]-Steuerelement, das eindeutige Funktionen bereitstellt.

In dieser exemplarischen Vorgehensweise wird gezeigt, wie Sie mithilfe von Code eine [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.MaskedTextBox?displayProperty=nameWithType>-Steuerelement auf einer [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Seite hosten.

Eine umfassende Code Auflistung der in dieser exemplarischen Vorgehensweise gezeigten Aufgaben finden Sie unter [Hosting a Windows Forms Control in WPF Sample](https://go.microsoft.com/fwlink/?LinkID=160057).

## <a name="prerequisites"></a>Erforderliche Voraussetzungen

Für diese exemplarische Vorgehensweise benötigen Sie Visual Studio.

## <a name="hosting-the-windows-forms-control"></a>Hosten des Windows Forms-Steuerelements

### <a name="to-host-the-maskedtextbox-control"></a>So hosten Sie das MaskedTextBox-Steuerelement

1. Erstellen Sie ein WPF-Anwendungsprojekt mit dem Namen `HostingWfInWpf`.

2. Fügen Sie Verweise auf die folgenden Assemblys hinzu.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. Öffnen Sie die Datei "MainWindow. XAML" im WPF-Designer.

4. Benennen Sie das <xref:System.Windows.Controls.Grid> Element `grid1`.

     [!code-xaml[HostingWfInWPF#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml#1)]

5. Wählen Sie in Designansicht-oder XAML-Ansicht das <xref:System.Windows.Window> Element aus.

6. Klicken Sie im Eigenschaftenfenster auf die Registerkarte **Ereignisse** .

7. Doppelklicken Sie auf das <xref:System.Windows.FrameworkElement.Loaded> Ereignis.

8. Fügen Sie den folgenden Code ein, um das <xref:System.Windows.FrameworkElement.Loaded>-Ereignis zu behandeln.

     [!code-csharp[HostingWfInWPF#10](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#10)]
     [!code-vb[HostingWfInWPF#10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#10)]

9. Fügen Sie am Anfang der Datei die folgende `Imports` oder `using` Anweisung hinzu.

     [!code-csharp[HostingWfInWPF#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingWfInWPF/CSharp/HostingWfInWPF/Window1.xaml.cs#11)]
     [!code-vb[HostingWfInWPF#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingWfInWPF/VisualBasic/HostingWfInWpf/Window1.xaml.vb#11)]

10. Drücken Sie **F5**, um die Anwendung zu erstellen und auszuführen.

## <a name="see-also"></a>Siehe auch

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Entwerfen von XAML-Code in Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Exemplarische Vorgehensweise: Hosten eines Windows Forms-Steuerelements in WPF mithilfe von XAML](walkthrough-hosting-a-windows-forms-control-in-wpf-by-using-xaml.md)
- [Exemplarische Vorgehensweise: Hosten eines zusammengesetzten Windows Forms-Steuerelements in WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Exemplarische Vorgehensweise: Hosten eines zusammengesetzten WPF-Steuerelements in Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Windows Forms-Steuerelemente und entsprechende WPF-Steuerelemente](windows-forms-controls-and-equivalent-wpf-controls.md)
- [Beispiel zum Hosten eines Windows Forms-Steuerelements in WPF](https://go.microsoft.com/fwlink/?LinkID=160057)
