---
ms.openlocfilehash: d888aba597cb6981828ca67fba04912cbcf7935f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567443"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Typen im Microsoft.VisualBasic.ApplicationServices-Namespace nicht verfügbar

Die Typen im <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>-Namespace sind nicht verfügbar.

#### <a name="version-introduced"></a>Eingeführt in Version

.NET Core 3.0 Preview 8

#### <a name="change-description"></a>Änderungsbeschreibung

Die Typen im <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>-Namespace waren in einigen Releases von .NET Core 3.0 Preview verfügbar. Ab .NET Core 3.0 Preview 9 sind sie nicht mehr verfügbar.

Die Typen wurden entfernt, um unnötige Assemblyabhängigkeiten oder Breaking Changes in nachfolgenden Releases zu vermeiden.

#### <a name="recommended-action"></a>Empfohlene Maßnahme

Wenn Sie für Ihren Code <xref:Microsoft.VisualBasic.ApplicationServices>-Typen und deren Member benötigen, können Sie möglicherweise einen entsprechenden Typ oder Member in der .NET-Klassenbibliothek verwenden. So stellen beispielsweise einige <xref:System.Environment?displayProperty=nameWithType>- und <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType>-Member entsprechende Funktionen für die Eigenschaften der <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType>-Klasse bereit.

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Betroffene APIs

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-- >

