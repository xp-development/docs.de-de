---
title: Dynamische Eigenschaften LINQ to XML Referenz
ms.date: 10/22/2019
ms.topic: reference
ms.openlocfilehash: 48b51e92eb78786b2cc189e3e7daa00875b41585
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73197053"
---
# <a name="linq-to-xml-dynamic-properties"></a>Dynamische Eigenschaften in LINQ to XML

Dieser Abschnitt enthält Referenzinformationen zu den dynamischen Eigenschaften in LINQ to XML. Diese Eigenschaften werden von den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement>im <xref:System.Xml.Linq>-Namespace verfügbar gemacht.

Wie im Artikel [Übersicht über die WPF-Datenbindung mit LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md) erläutert, gibt es für jede dynamische Eigenschaft in derselben Klasse eine entsprechende öffentliche Standardeigenschaft oder -methode. Diese Standardmember können für die Mehrzahl der Fälle eingesetzt werden. Die dynamischen Eigenschaften werden speziell für LINQ to XML-Datenbindungsszenarios bereitgestellt. Weitere Informationen zu den Standardmembern dieser Klassen finden Sie in den Referenzthemen zu den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement>.

Die dynamischen Eigenschaften in diesem Abschnitt lassen sich hinsichtlich ihrer aufgelösten Werte in zwei Kategorien einteilen:

- einfache dynamische Eigenschaften, wie die `Value`-Eigenschaften in den Klassen <xref:System.Xml.Linq.XAttribute> und <xref:System.Xml.Linq.XElement>, die einen einzelnen Wert ergeben

- Indizierte Werte, wie die Eigenschaften [Elements](elements-xelement-dynamic-property.md) und [Descendants](descendants-xelement-dynamic-property.md) der <xref:System.Xml.Linq.XElement>-Klasse, die einen Indexertyp ergeben. Damit der Indexertyp den gewünschten Wert bzw. die gewünschte Auflistung ergibt, muss ihm ein erweiterter Namensparameter übergeben werden.

Alle dynamischen Eigenschaften, die einen indizierten Wert des Typs <xref:System.Collections.Generic.IEnumerable%601> zurückgeben, arbeiten mit verzögerter Ausführung. Weitere Informationen zur verzögerten Ausführung finden Sie unter [Einführung in LINQ-Abfragen (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).

## <a name="reference"></a>Referenz

- <xref:System.Xml.Linq>
- <xref:System.Xml.Linq.XElement?displayProperty=fullName>
- <xref:System.Xml.Linq.XAttribute?displayProperty=fullName>

## <a name="see-also"></a>Siehe auch

- [WPF-Datenbindung mit LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md)
- [Übersicht über WPF-Datenbindung mit LINQ to XML](wpf-data-binding-with-linq-to-xml-overview.md)
- [Einführung in LINQ-Abfragen (C#)](../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
