---
title: Benutzeroberflächenautomatisierungs-Unterstützung für den Separator-Steuerelementtyp
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Separator control type
- Separator control type
- control types, Separator
ms.assetid: 89f42247-c699-4afa-91e1-2baaf0d86c9d
ms.openlocfilehash: 2f2b68b2d36d49313f443e1d49776ecb4feb16fe
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800254"
---
# <a name="ui-automation-support-for-the-separator-control-type"></a>Benutzeroberflächenautomatisierungs-Unterstützung für den Separator-Steuerelementtyp
> [!NOTE]
> Diese Dokumentation ist für .NET Framework-Entwickler vorgesehen, die die verwalteten [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]-Klassen verwenden möchten, die im <xref:System.Windows.Automation>-Namespace definiert sind. Aktuelle Informationen zur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]finden Sie auf der Seite zur [Windows-Automatisierungs-API: UI-Automatisierung](/windows/win32/winauto/entry-uiauto-win32).  
  
 Dieses Thema enthält Informationen zur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Unterstützung für den Steuerelementtyp „Separator“. In [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umfasst ein Steuerelementtyp eine Reihe von Bedingungen, die ein Steuerelement erfüllen muss, damit die <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> -Eigenschaft verwendet werden kann. Die Bedingungen schließen bestimmte Richtlinien für [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Struktur, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Eigenschaftswerte und Steuerelementmuster ein.  
  
 Mithilfe von Separator-Steuerelementen wird ein Bereich visuell in zwei Abschnitte unterteilt. Ein Separator-Steuerelement kann z. B. eine Leiste sein, die zwei Bereiche in einem Fenster definiert. Wenn die Trennlinie verschoben werden kann, sollte das Steuerelement als Steuerelementtyp „Thumb“ verfügbar gemacht werden.  
  
 In den folgenden Abschnitten werden die [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Struktur, -Eigenschaften, -Steuerelementmuster und -Ereignisse definiert, die für den Steuerelementtyp „Separator“ erforderlich sind. Die [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Anforderungen gelten für alle Listensteuerelemente in [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]oder [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Erforderliche Benutzeroberflächenautomatisierungs-Struktur  
 In der folgenden Tabelle werden die Steuerelementansicht und die Inhaltsansicht der [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Struktur für Separator-Steuerelemente sowie die möglichen Inhalte der Ansichten beschrieben. Weitere Informationen zur [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Struktur finden Sie unter [UI Automation Tree Overview](ui-automation-tree-overview.md).  
  
|Steuerelementansicht|Inhaltsansicht|  
|------------------|------------------|  
|Trennzeichen|-Das Trennzeichen Steuerelement hat niemals Inhalt.|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Erforderliche Benutzeroberflächenautomatisierungs-Eigenschaften  
 Die folgende Tabelle enthält die [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Eigenschaften, deren Werte oder Definitionen für Separator-Steuerelemente besonders relevant sind. Weitere Informationen zu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Eigenschaften finden Sie unter [Benutzeroberflächenautomatisierungs-Eigenschaften für Clients](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Eigenschaft|{2&gt;Wert&lt;2}|Hinweise|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Siehe Hinweise.|Der Wert dieser Eigenschaft muss für alle Steuerelemente in einer Anwendung eindeutig sein.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Siehe Hinweise.|Das äußere Rechteck, das das gesamte Steuerelement enthält.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Siehe Hinweise.|Unterstützt, wenn es ein umschließendes Rechteck gibt. Wenn nicht auf jeden Punkt innerhalb des umschließenden Rechtecks geklickt werden kann, und Sie spezielle Treffertests ausführen, setzen Sie die Eigenschaft außer Kraft, und stellen Sie dann einen klickbaren Punkt bereit.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Siehe Hinweise.|Wenn das Steuerelement den Tastaturfokus erhalten kann, muss es diese Eigenschaft unterstützen.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|""|Das Separator-Steuerelement erfordert kein „NameProperty“.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`null`|Das Separator-Steuerelement hat keine statische Bezeichnung.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Trennzeichen|Dieser Wert ist für alle Benutzeroberflächenframeworks gleich.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|„Trennlinie“|Lokalisierte Zeichenfolge für den Steuerelementtyp „Separator“.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Falsch|Das Separator-Steuerelement ist nie ein Inhaltselement.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Das Separator-Steuerelement muss immer ein Steuerelement sein.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Erforderliche Benutzeroberflächenautomatisierungs-Steuerelementmuster  
 Das Separator-Steuerelement ist nicht erforderlich, um Steuerelementmuster zu unterstützen.  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Erforderliche Benutzeroberflächenautomatisierungs-Ereignisse  
 Die folgende Tabelle enthält die [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Ereignisse, die von allen Separator-Steuerelementen unterstützt werden müssen. Weitere Informationen zu Ereignissen finden Sie unter [UI Automation Events Overview](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] -Ereignis|-Unterstützung|Hinweise|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|Durch geänderte<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> -Eigenschaft ausgelöstes Ereignis.|Erforderlich|Keine|  
|Durch geänderte<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> -Eigenschaft ausgelöstes Ereignis.|Erforderlich|Keine|  
|Durch geänderte<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> -Eigenschaft ausgelöstes Ereignis.|Erforderlich|Keine|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Erforderlich|Keine|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Erforderlich|Keine|  
  
## <a name="see-also"></a>Siehe auch

- <xref:System.Windows.Automation.ControlType.Separator>
- [Übersicht über Steuerelementtypen für Benutzeroberflächenautomatisierung](ui-automation-control-types-overview.md)
- [Übersicht über die Benutzeroberflächenautomatisierung](ui-automation-overview.md)
