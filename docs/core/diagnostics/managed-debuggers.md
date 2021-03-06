---
title: Verwaltete Debugger – .NET Core
description: Eine Übersicht über die verwalteten Debugger in Visual Studio und Visual Studio Code.
author: sdmaclea
ms.author: stmaclea
ms.date: 08/05/2019
ms.openlocfilehash: 3741011d22ab6c4240b7f88a9ab790ea61ecd0d2
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2019
ms.locfileid: "72303647"
---
# <a name="net-core-managed-debuggers"></a>Verwaltete Debugger in .NET Core

Mithilfe von Debuggern können Programme angehalten oder Schritt für Schritt ausgeführt werden. Nach dem Anhalten kann der aktuelle Status des Prozesses angezeigt werden. Indem Sie wesentliche Abschnitte schrittweise durchlaufen, erhalten Sie einen Einblick in Ihren Code und die Gründe für das erzeugte Ergebnis.

Microsoft stellt in **Visual Studio** und **Visual Studio Code** Debugger für verwalteten Code bereit.

## <a name="visual-studio-managed-debugger"></a>Verwalteter Debugger von Visual Studio

**Visual Studio**  ist eine integrierte Entwicklungsumgebung, die den umfassendsten Debugger bereitstellt. Visual Studio ist eine hervorragende Wahl für Entwickler, die unter Windows arbeiten.

- [Tutorial: Debuggen einer .NET Core-Anwendung unter Windows mit Visual Studio](../tutorials/debugging-with-visual-studio.md)

Obwohl Visual Studio eine Windows-Anwendung ist, können hiermit auch Linux- und macOS-Apps remote debuggt werden.

- [Debuggen einer .NET Core-Anwendung unter Linux/OS X mit Visual Studio](https://github.com/Microsoft/MIEngine/wiki/Offroad-Debugging-of-.NET-Core-on-Linux---OSX-from-Visual-Studio)

 Für das Debuggen von ASP.NET Core-Apps gelten leicht abweichende Anweisungen.

- [Debuggen von ASP.NET-Apps in Visual Studio](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications#debug-aspnet-core-apps)

## <a name="visual-studio-code-managed-debugger"></a>Verwalteter Debugger von Visual Studio Code

**Visual Studio Code** ist ein einfacher Code-Editor für alle Plattformen. Er nutzt die gleiche Implementierung des .NET Core-Debuggers wie Visual Studio, jedoch mit einer vereinfachten Benutzeroberfläche.

- [Tutorial: Debuggen einer .NET Core-Anwendung mit Visual Studio Code](../tutorials/with-visual-studio-code.md#debug)
- [Debuggen in Visual Studio Code](https://code.visualstudio.com/docs/editor/debugging)
