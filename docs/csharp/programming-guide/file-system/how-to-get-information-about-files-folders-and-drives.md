---
title: 'Vorgehensweise: Abrufen von Informationen über Dateien, Ordner und Laufwerke – C#-Programmierhandbuch'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
ms.openlocfilehash: 57c7811246dd1de3f009033403ec269082915c09
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590024"
---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Vorgehensweise: Abrufen von Informationen über Dateien, Ordner und Laufwerke (C#-Programmierhandbuch)
Sie können im .NET Framework auf die Dateisysteminformationen mithilfe folgender Klassen zugreifen:  
  
- <xref:System.IO.FileInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DirectoryInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.DriveInfo?displayProperty=nameWithType>  
  
- <xref:System.IO.Directory?displayProperty=nameWithType>  
  
- <xref:System.IO.File?displayProperty=nameWithType>  
  
 Die Klassen <xref:System.IO.FileInfo> und <xref:System.IO.DirectoryInfo> stehen für eine Datei oder ein Verzeichnis, und sie enthalten Eigenschaften, die viele der Dateiattribute offen legen, die vom NTFS-Dateisystem unterstützt werden. Sie enthalten zusätzlich Methoden zum Öffnen, Schließen, Bewegen und Löschen von Dateien und Ordnern. Sie können Instanzen dieser Klassen erstellen, indem Sie eine Zeichenfolge in den Konstruktor übergeben, die den Namen der Datei, des Ordners oder des Laufwerks repräsentiert:  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Sie können auch die Namen von Dateien, Ordnern oder Laufwerken abrufen, indem Sie Aufrufe auf <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=nameWithType>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=nameWithType> und <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=nameWithType> verwenden.  
  
 Die Klassen <xref:System.IO.Directory?displayProperty=nameWithType> und <xref:System.IO.File?displayProperty=nameWithType> bieten statische Methoden zum Abrufen von Informationen über Verzeichnisse und Dateien.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel veranschaulicht verschiedene Arten des Zugriffs auf Datei- und Ordnerinformationen.  
  
 [!code-csharp[csFilesandFolders#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#6)]  
  
## <a name="robust-programming"></a>Stabile Programmierung  
 Beim Verarbeiten von benutzerdefinierten Pfadzeichenfolgen, sollten Sie auch die Ausnahmen für folgende Bedingungen bearbeiten:  
  
- Der Dateiname ist falsch formatiert. Er enthält beispielsweise ungültige Zeichen oder besteht nur aus Leerzeichen.  
  
- Der Dateiname ist NULL.  
  
- Der Dateiname übersteigt die vom System definierte Maximallänge.  
  
- Der Dateiname enthält einen Doppelpunkt (:).  
  
 Wenn die Anwendung nicht die notwendigen Leseberechtigungen für die angegebene Datei hat, gibt die `Exists`-Methode `false` zurück, unabhängig davon, ob ein Pfad vorhanden ist; die Methode löst keine Ausnahme aus.  
  
## <a name="see-also"></a>Siehe auch

- <xref:System.IO?displayProperty=nameWithType>
- [C#-Programmierhandbuch](../index.md)
- [Das Dateisystem und die Registrierung (C#-Programmierhandbuch)](./index.md)
