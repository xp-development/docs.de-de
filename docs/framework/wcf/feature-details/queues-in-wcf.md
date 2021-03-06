---
title: Warteschlangen in Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- queues [WCF]
ms.assetid: 43008409-1bb4-4bd4-85d7-862c8f10ae20
ms.openlocfilehash: e921084ed28cb4e846cb269e57e58a194e9437a5
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837336"
---
# <a name="queues-in-windows-communication-foundation"></a>Warteschlangen in Windows Communication Foundation
In den Themen in diesem Abschnitt wird Windows Communication Foundation (WCF)-Unterstützung für Warteschlangen beschrieben. WCF bietet Unterstützung für Warteschlangen, indem Microsoft Message Queuing (früher als MSMQ bezeichnet) als Transport genutzt wird, und ermöglicht die folgenden Szenarien:  
  
- Lose verbundene Anwendungen: Die sendenden Anwendungen können Nachrichten an Warteschlangen senden, unabhängig davon, ob die empfangende Anwendung für die Verarbeitung der Nachricht zur Verfügung steht. Die Warteschlange macht die Verarbeitung unabhängig. So kann die sendende Anwendung Nachrichten mit einer Frequenz an die Warteschlange senden, die unabhängig davon ist, wie schnell die empfangenden Anwendungen die Nachrichten verarbeiten können. Die Gesamtverfügbarkeit des Systems verbessert sich, wenn das Senden von Nachrichten an eine Warteschlange und die Nachrichtenverarbeitung nur lose miteinander verbunden sind.  
  
- Fehlerisolierung: Anwendungen, die Nachrichten an eine Warteschlange senden oder Nachrichten empfangen, können fehlschlagen, ohne dass dies Auswirkungen auf die anderen Anwendungen hat. Wenn beispielsweise in der empfangenden Anwendung ein Fehler auftritt, kann die sendende Anwendung trotzdem weiterhin Nachrichten an die Warteschlange senden. Sobald der Empfänger wieder einsatzbereit ist, können die Nachrichten in der Warteschlange verarbeitet werden. Durch die Fehlerisolierung werden Zuverlässigkeit und Verfügbarkeit des Systems insgesamt verbessert.  
  
- Lastenausgleich: Sendende Anwendungen können empfangende Anwendungen mit Nachrichten überlasten. Durch Warteschlangen kann ein Ungleichgewicht an gesendeten und verarbeiteten Nachrichten ausgeglichen werden, sodass der Empfänger nicht mit Nachrichten überschwemmt wird.  
  
- Getrennte Vorgänge: Die Vorgänge des Sendens, Empfangens und Verarbeitens können bei der Kommunikation über Netzwerke mit hoher Latenz oder eingeschränkter Verfügbarkeit, wie dies zum Beispiel bei mobilen Geräten der Fall ist, voneinander getrennt werden. Warteschlangen ermöglichen die Fortsetzung dieser Vorgänge, selbst wenn die Endpunkte nicht erreichbar sind. Sobald die Verbindung wiederhergestellt ist, leitet die Warteschlange die Nachrichten an die empfangende Anwendung weiter.  
  
 Wenn Sie die Warteschlangen Funktion in einer WCF-Anwendung verwenden möchten, können Sie eine der Standard Bindungen verwenden, oder Sie können eine benutzerdefinierte Bindung erstellen, wenn eine der Standard Bindungen Ihre Anforderungen nicht erfüllt. Weitere Informationen über relevante Standard Bindungen und deren Auswahl finden Sie unter Vorgehens [Weise: Austauschen von Nachrichten mit WCF-Endpunkten und Message Queuing Anwendungen](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md). Weitere Informationen zum Erstellen benutzerdefinierter Bindungen finden Sie unter [Benutzerdefinierte Bindungen](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Warteschlangenübersicht](../../../../docs/framework/wcf/feature-details/queues-overview.md)  
 Eine Übersicht über die Konzepte des Message Queuings (Nachrichtenwarteschlangen).  
  
 [Queuing in WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 Eine Übersicht über die Unterstützung von WCF-Warteschlangen.  
  
 [Vorgehensweise: Austauschen von Nachrichten in einer Warteschlange mit WCD-Endpunkten](../../../../docs/framework/wcf/feature-details/how-to-exchange-queued-messages-with-wcf-endpoints.md)  
 Erläutert, wie die <xref:System.ServiceModel.NetMsmqBinding>-Klasse für die Kommunikation zwischen einem WCF-Client und einem WCF-Dienst verwendet wird.  
  
 [Vorgehensweise: Nachrichtenaustausch mit WCF-Endpunkten und Message Queuing-Anwendungen](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 Erläutert die Verwendung der <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> für die Kommunikation zwischen WCF-und Message Queuing-Anwendungen.  
  
 [Gruppieren von Nachrichten in der Warteschlange einer Sitzung](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)  
 Erläutert, wie Nachrichten in einer Warteschlange gruppiert werden können, um die Verarbeitung zusammengehöriger Nachrichten durch eine einzelne Empfängeranwendung zu erleichtern.  
  
 [Batchverarbeitung von Nachrichten in einer Transaktion](../../../../docs/framework/wcf/feature-details/batching-messages-in-a-transaction.md)  
 Erläutert die Batchverarbeitung von Nachrichten in einer Transaktion.  
  
 [Verwenden von Warteschlangen für unzustellbare Nachrichten zur Handhabung von Nachrichtenübertragungsfehlern](../../../../docs/framework/wcf/feature-details/using-dead-letter-queues-to-handle-message-transfer-failures.md)  
 Erläutert die Handhabung von Nachrichtenübertragungen und Sendefehlern mithilfe von Warteschlangen für unzustellbare Nachrichten und beschreibt, wie Nachrichten in der Warteschlange für unzustellbare Nachrichten verarbeitet werden.  
  
 [Behandlung nicht verarbeitbarer Nachrichten](../../../../docs/framework/wcf/feature-details/poison-message-handling.md)  
 Erläutert den Umgang mit beschädigten (nicht verarbeitbaren) Nachrichten, das heißt Nachrichten, die auch nach der maximalen Anzahl von Versuchen nicht an die Empfängeranwendung gesendet werden konnten.  
  
 [Unterschiede zwischen den Warteschlangenfunktionen in Windows Vista, Windows Server 2003 und Windows XP](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)  
 Fasst die Unterschiede in der WCF-Warteschlangen Funktion zwischen Windows Vista, [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]und [!INCLUDE[wxp](../../../../includes/wxp-md.md)]zusammen.  
  
 [Sichern von Nachrichten mit Transportsicherheit](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)  
 Beschreibt, wie Nachrichten in Warteschlangen mithilfe der Transportsicherheit geschützt werden können.  
  
 [Sichern von Nachrichten mithilfe der Nachrichtensicherheit](../../../../docs/framework/wcf/feature-details/securing-messages-using-message-security.md)  
 Beschreibt, wie Nachrichten in Warteschlangen mithilfe der Nachrichtensicherheit geschützt werden können.  
  
 [Problembehandlung bei Nachrichtenwarteschlangen](../../../../docs/framework/wcf/feature-details/troubleshooting-queued-messaging.md)  
 Beschreibt, wie allgemeine Warteschlangenprobleme behoben werden können.  
  
 [Bewährte Methoden für die Kommunikation unter Verwendung von Warteschlangen](../../../../docs/framework/wcf/feature-details/best-practices-for-queued-communication.md)  
 Erläutert bewährte Methoden für die Verwendung der WCF-Warteschlangen Kommunikation.  
