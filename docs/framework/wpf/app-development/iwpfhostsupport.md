---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 91a29233d12a842a64b7d3dd497312f6dc6742ca
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423649"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Anwendungen, die [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Inhalt über "PresentationHost. exe" hosten, implementieren diese Schnittstelle, um einen Punkt der Integration zwischen dem Host und "PresentationHost. exe" bereitzustellen.  
  
## <a name="remarks"></a>Hinweise  
 [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] Anwendungen, wie z. b. Webbrowser, können WPF-Inhalte hosten, einschließlich XAML-Browser Anwendungen (XBAPs) und losem XAML-Code. Zum Hosten von WPF-Inhalt erstellen [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] Anwendungen eine Instanz des [Webbrowser-Steuer](https://go.microsoft.com/fwlink/?LinkId=97911)Elements. Um gehostet zu werden, erstellt WPF eine Instanz von "PresentationHost. exe", die den gehosteten WPF-Inhalt für den Host zur Anzeige im [Webbrowser-Steuer](https://go.microsoft.com/fwlink/?LinkId=97911)Element bereitstellt.  
  
 Die durch `IWpfHostSupport` aktivierte Integration ermöglicht PresentationHost. exe Folgendes:  
  
- Ermitteln und registrieren Sie sich bei den roheingabe Geräten (Human Interface Devices), an denen die Host Anwendung interessiert ist.  
  
- Empfangen von Eingabe Nachrichten von den registrierten roheingabe-Geräten und weiterleiten entsprechender Nachrichten an die Host Anwendung.  
  
- Fragen Sie die Host Anwendung nach Benutzeroberflächen für benutzerdefinierte Fortschritte und Fehler ab.  
  
> [!NOTE]
> Diese API ist nur für die Verwendung auf dem lokalen Clientcomputer vorgesehen und wird nur zu diesem Zweck unterstützt.  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Ermöglicht es der Datei "PresentationHost.exe", Geräte für die Eingabe von Rohdaten (Eingabegeräte, Human Interface Devices) zu erkennen, die für die Hostanwendung interessant sind.|  
|[FilterInputMessage](filterinputmessage.md)|Wird immer dann von "PresentationHost.exe" aufgerufen, wenn eine Meldung empfangen wurde, es sei denn, E_NOTIMPL wurde zurückgegeben.|  
|[GetCustomUI](getcustomui.md)|PresentationHost. exe bietet standardmäßig einen eigenen Bereitstellungs Fortschritt und Bereitstellungs Fehler-Benutzeroberflächen, die beim Bereitstellen von WPF-Inhalt angezeigt werden.|
