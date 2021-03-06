---
title: SourceLink und .NET-Bibliotheken
description: Empfehlungen für bewährte Methoden zum Verwenden von SourceLink zur Verbesserung des Debuggens für .NET-Bibliotheken.
author: jamesnk
ms.author: mairaw
ms.date: 01/15/2019
ms.openlocfilehash: 89f9e3b1fd70003c528465f29a143b157468d539
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089285"
---
# <a name="source-link"></a>SourceLink

SourceLink ist eine Technologie, mit der Entwickler Quellcode aus .NET-Assemblys über NuGet debuggen können. SourceLink wird beim Erstellen des NuGet-Pakets ausgeführt und bettet Metadaten der Quellcodeverwaltung in Assemblys und das Paket ein. Entwickler, die das Paket herunterladen und SourceLink in Visual Studio aktiviert haben, können den Quellcode schrittweise ausführen. SourceLink bietet Metadaten zur Quellcodeverwaltung, um das Debuggen zu optimieren.

## <a name="source-link-demo"></a>SourceLink-Demo

> [!VIDEO https://www.youtube.com/embed/gyRGhCQPkB4?start=61]

## <a name="using-source-link"></a>Verwenden von SourceLink

Anweisungen zum Verwenden von SourceLink finden Sie im GitHub-Repository [dotnet/sourcelink](https://github.com/dotnet/sourcelink/blob/master/README.md).

Sie können mit dem [NuGet-Paket-Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) bestätigen, dass die SourceLink-Metadaten erfolgreich in das Paket eingebettet wurden. Überprüfen Sie, ob die `Repository`-Metadaten über eine Commit-ID verfügen, und ob sich PDB-Dateien in der jeweiligen DLL-Zieldatei befinden.

![Quellenlink im NuGet-Paket-Explorer](./media/sourcelink/nuget-package-explorer-sourcelink.png "Quellenlink im NuGet-Paket-Explorer")

**✔️ ERWÄGEN SIE**, mit SourceLink ggf. Metadaten der Quellcodeverwaltung Ihren Assemblys und NuGet-Paketen hinzuzufügen.

> [!TIP]
> Sie können für Entwickler den Debugvorgang weiter verbessern, indem Sie Ihren Typen Debuggerattribute hinzufügen.
>
> * <xref:System.Diagnostics.DebuggerDisplayAttribute> kann anpassen, wie eine Klasse oder ein Feld in den Variablenfenstern des Debuggers angezeigt wird.
> * <xref:System.Diagnostics.DebuggerStepThroughAttribute> weist den Debugger an, schrittweise durch den Code zu laufen, anstatt ihn schrittweise auszuführen.
> * <xref:System.Diagnostics.DebuggerBrowsableAttribute> bestimmt, ob und wie ein Member in Debuggervariablenfenstern angezeigt wird.

**✔️ ERWÄGEN SIE** das Veröffentlichen von Symboldateien (`*.pdb`).

> Für das beste Debugergebnis sollte Ihre Bibliothek sowohl Symboldateien veröffentlichen als auch SourceLink verwenden. Weitere Informationen zu Symboldateien und Symbolpaketen finden Sie unter [Symbolpakete](./nuget.md#symbol-packages).

>[!div class="step-by-step"]
>[Zurück](dependencies.md)
>[Weiter](publish-nuget-package.md)
