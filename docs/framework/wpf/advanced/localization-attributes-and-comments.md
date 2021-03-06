---
title: Lokalisierungsattribute und -kommentare
ms.date: 03/30/2017
helpviewer_keywords:
- localization [WPF], attributes
- localization [WPF], comments
ms.assetid: ead2d9ac-b709-4ec1-a924-39927a29d02f
ms.openlocfilehash: 4f9c2700d8163988b7ea1e75bec1427778cf571c
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004896"
---
# <a name="localization-attributes-and-comments"></a>Lokalisierungsattribute und -kommentare
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]-Lokalisierungs Kommentare sind Eigenschaften im XAML-Quellcode, die von Entwicklern zur Bereitstellung von Regeln und Hinweisen für die Lokalisierung bereitgestellt werden. [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]-Lokalisierungkommentare enthalten zwei Arten von Informationen: Lokalisierbarkeitsattribute und formfreie Lokalisierungskommentare. Lokalisierbarkeitsattribute werden von der [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-Lokalisierungs-API verwendet, um anzugeben, welche Ressourcen lokalisiert werden sollen. Formfreie Kommentare umfassen alle Informationen, die der Anwendungsentwickler beinhaltet haben möchte.  

<a name="Localizer_Comments_"></a>   
## <a name="localization-comments"></a>Lokalisierungskommentare  
 Wenn Markup Anwendungs Autoren Anforderungen für bestimmte Elemente in XAML haben, z. b. Einschränkungen der Textlänge, Schriftfamilie oder Schriftgröße, können Sie diese Informationen an Lokalisierer mit Kommentaren im XAML-Code weiterleiten. Das Hinzufügen von Kommentaren zu Quellcode funktioniert wie folgt:  
  
1. Anwendungsentwickler fügen dem XAML-Quellcode Lokalisierungs Kommentare hinzu.  
  
2. Während des Buildprozesses können Sie in der PROJ-Datei angeben, ob die formfreien Lokalisierungskommentare in der Assembly bleiben oder ob ein Teil der oder alle Kommentare entfernt werden sollen. Die entfernten Kommentare werden in einer separaten Datei abgelegt. Sie geben die Option mit einem `LocalizationDirectivesToLocFile`-Tag an, z.B.:  
  
     `<LocalizationDirectivesToLocFile>` *Wert* `</LocalizationDirectivesToLocFile>`  
  
3. Folgende Werte können zugewiesen werden:  
  
    - **None** – Sowohl Kommentare als auch Attribute bleiben in der Assembly. Es wird keine separate Datei generiert.  
  
    - **CommentsOnly** – Es werden nur die Kommentare aus der Assembly entfernt und in der separaten LocFile abgelegt.  
  
    - **Alle** – Es werden sowohl Kommentare als auch Attribute aus der Assembly entfernt und in einer separaten LocFile abgelegt.  
  
4. Wenn lokalisierbare Ressourcen aus BAML extrahiert werden, werden die Lokalisier barkeits Attribute von der BAML-Lokalisierungs-API berücksichtigt.  
  
5. Lokalisierungskommentardateien, die nur formfreie Kommentare enthalten, werden zu einem späteren Zeitpunkt in den Lokalisierungsprozess integriert.  
  
 Im folgenden Beispiel wird gezeigt, wie Sie einer XAML-Datei Lokalisierungs Kommentare hinzufügen.  
  
 `<TextBlock x:Id = "text01"`  
  
 `FontFamily = "Microsoft Sans Serif"`  
  
 `FontSize = "12"`  
  
 `Localization.Attributes = "$Content (Unmodifiable Readable Text)`  
  
 `FontFamily (Unmodifiable Readable)"`  
  
 `Localization.Comments = "$Content (Trademark)`  
  
 `FontSize (Trademark font size)" >`  
  
 `Microsoft`  
  
 `</TextBlock>`  
  
 Im vorherigen Beispiel enthält der Localization.Attributes-Abschnitt die Lokalisierungsattribute und der Localization.Comments-Abschnitt die formfreien Kommentare. Die folgenden Tabellen zeigen Attribute und Kommentare sowie deren Bedeutung für den Lokalisierungsexperten.  
  
|Lokalisierungsattribute|Bedeutung|  
|-----------------------------|-------------|  
|$Content (Unmodifiable Readable Text)|Der Inhalt des TextBlock-Elements kann nicht geändert werden. Lokalisierungsexperten können das Wort „Microsoft“ nicht ändern. Der Inhalt ist für den Lokalisierungsexperten sichtbar (Readable). Die Kategorie des Inhalts ist Text.|  
|FontFamily (Unmodifiable Readable)|Die FontFamily-Eigenschaft des TextBlock-Elements kann nicht geändert werden, ist aber für den Lokalisierungsexperten sichtbar.|  
  
|Formfreie Lokalisierungskommentare|Bedeutung|  
|--------------------------------------|-------------|  
|$Content (Trademark)|Der Anwendungsentwickler teilt dem Lokalisierungsexperten mit, dass der Inhalt im TextBlock-Element eine Marke ist.|  
|FontSize (Trademark font size)|Der Anwendungsentwickler gibt an, dass die FontSize-Eigenschaft der Standardmarkengröße entsprechen soll.|  
  
### <a name="localizability-attributes"></a>Lokalisierungsattribute  
 Die Informationen in Localization.Attributes enthalten eine Liste von Paaren: den Namen des Zielwerts und die zugeordneten Lokalisierungswerte. Der Zielname kann ein Eigenschaftenname oder der spezielle $Content-Name sein. Wenn es sich um einen Eigenschaftennamen handelt, ist der Zielwert der Wert der Eigenschaft. Wenn es sich um $Content handelt, ist der Zielwert der Inhalt des Elements.  
  
 Es gibt drei Typen von Attributen:  
  
- **Category**. Gibt an, ob ein Wert in einem Lokalisierungstool geändert werden kann. Siehe <xref:System.Windows.LocalizabilityAttribute.Category%2A>.  
  
- **Lesbarkeit**. Gibt an, ob ein Lokalisierungstool einen Wert lesen (und anzeigen) kann. Siehe <xref:System.Windows.LocalizabilityAttribute.Readability%2A>.  
  
- **Änderbarkeit**. Gibt an, ob ein Lokalisierungstool das Ändern eines Werts zulässt. Siehe <xref:System.Windows.LocalizabilityAttribute.Modifiability%2A>.  
  
 Diese Attribute können in jeder Reihenfolge durch ein Leerzeichen getrennt angegeben werden. Falls doppelte Attribute angegeben werden, überschreibt das letzte Attribut die vorherigen Attribute. So legt Localization.Attributes = "Unmodifiable Modifiable" beispielsweise Modifiability auf Modifiable fest, da es sich hierbei um den letzten Wert handelt.  
  
 Bearbeitbarkeit und Lesbarkeit sind selbsterklärend. Das Category-Attribut stellt vordefinierte Kategorien bereit, die den Lokalisierungsexperten beim Übersetzen von Text unterstützen. Kategorien wie Text, Label und Title geben dem Lokalisierungsexperten Informationen zum Übersetzen des Texts. Es gibt auch spezielle Kategorien: None, Vererbung, ignorieren und NeverLocalize.  
  
 In der folgenden Tabelle werden die Bedeutung der speziellen Kategorien erläutert.  
  
|Kategorie|Bedeutung|  
|--------------|-------------|  
|None|Der Zielwert besitzt keine definierte Kategorie.|  
|Inherit|Der Zielwert erbt seine Kategorie von seinem übergeordneten Element.|  
|Ignorieren|Der Zielwert wird im Lokalisierungsprozess ignoriert. Ignore wirkt sich nur auf den aktuellen Wert aus. Untergeordnete Knoten werden nicht beeinflusst.|  
|NeverLocalize|Der aktuelle Wert kann nicht lokalisiert werden. Diese Kategorie wird von den untergeordneten Elementen eines Elements geerbt.|  
  
<a name="Localization_Comments"></a>   
## <a name="localization-comments"></a>Lokalisierungskommentare  
 Localization.Comments enthält formfreie Zeichenfolgen, die den Zielwert betreffen. Anwendungsentwickler können Informationen hinzufügen, um Lokalisierungsexperten Hinweise zur Übersetzung des Anwendungstexts zu geben. Das Format der Kommentare kann jede Zeichenfolge sein, die von „()“ umgeben ist. Verwenden Sie '\\' als Escapezeichen.  
  
## <a name="see-also"></a>Siehe auch

- [Globalisierung für WPF](globalization-for-wpf.md)
- [Verwenden des automatischen Layouts zum Erstellen einer Schaltfläche](how-to-use-automatic-layout-to-create-a-button.md)
- [Verwenden eines Rasters für automatisches Layout](how-to-use-a-grid-for-automatic-layout.md)
- [Lokalisieren einer Anwendung](how-to-localize-an-application.md)
