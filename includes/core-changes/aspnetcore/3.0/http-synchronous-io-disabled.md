---
ms.openlocfilehash: c861d61cbbe8075db4b17a702e863336ea621f2b
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198441"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP: Synchrones E/A auf allen Servern deaktiviert

Ab ASP.NET Core 3.0 sind synchrone Servervorgänge standardmäßig deaktiviert.

#### <a name="change-description"></a>Änderungsbeschreibung

`AllowSynchronousIO` ist eine Option auf sämtlichen Servern, die synchrone E/A-APIs wie `HttpRequest.Body.Read`, `HttpResponse.Body.Write` und `Stream.Flush` aktiviert bzw. deaktiviert. Diese APIs waren schon länger Ursache für fehlende Threads und hängende Apps. Ab ASP.NET Core 3.0 Preview 3 sind diese synchronen Vorgänge standardmäßig deaktiviert.

Betroffene Server:

- Kestrel
- HttpSys
- IIS In-Process
- TestServer

Erwartbare Fehler:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

Jeder Server verfügt über eine `AllowSynchronousIO`-Option, die dieses Verhalten steuert und nun standardmäßig `false` ist.

Das Verhalten kann auch auf Anforderung als vorübergehende Entschärfung überschrieben werden. Beispiel:

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

Wenn Sie Probleme mit einem `TextWriter` oder einem anderen Stream haben, der eine synchrone API in `Dispose` aufruft, rufen Sie stattdessen die neue `DisposeAsync`-API auf.

Weitere Informationen finden Sie unter [aspnet/AspNetCore#7644](https://github.com/aspnet/AspNetCore/issues/7644).

#### <a name="version-introduced"></a>Eingeführt in Version

3.0

#### <a name="old-behavior"></a>Altes Verhalten

`HttpRequest.Body.Read`, `HttpResponse.Body.Write` und `Stream.Flush` waren standardmäßig zulässig.

#### <a name="new-behavior"></a>Neues Verhalten

Diese synchronen APIs sind nun standardmäßig nicht mehr zulässig:

Erwartbare Fehler:

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>Grund für die Änderung

Diese synchronen APIs waren schon länger Ursache für fehlende Threads und hängende Apps. Ab ASP.NET Core 3.0 Preview 3 sind synchrone Vorgänge standardmäßig deaktiviert.

#### <a name="recommended-action"></a>Empfohlene Maßnahme

Verwenden Sie die asynchronen Versionen der Methoden. Das Verhalten kann auch auf Anforderung als vorübergehende Entschärfung überschrieben werden.

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Betroffene APIs

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
