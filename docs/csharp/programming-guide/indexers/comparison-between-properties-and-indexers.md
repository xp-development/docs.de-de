---
title: Vergleich zwischen Eigenschaften und Indexern – C#-Programmierhandbuch
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], vs. indexers
- indexers [C#], vs. properties
ms.assetid: 3358a89f-44a0-4a4d-bf8c-07237a90af39
ms.openlocfilehash: 4a14c2bf80ff203c5db7fc7663afeb816dc4a2c0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589470"
---
# <a name="comparison-between-properties-and-indexers-c-programming-guide"></a>Vergleich zwischen Eigenschaften und Indexern (C#-Programmierhandbuch)
Indexer sind wie Eigenschaften. Mit Ausnahme der in der folgenden Tabelle aufgeführten Unterschiede gelten alle für Eigenschaftenaccessoren definierten Regeln auch für Indexeraccessoren.  
  
|Eigenschaft|Indexer|  
|--------------|-------------|  
|Damit können Methoden wie allgemein zugängliche Datenmember aufgerufen werden.|Damit können Elemente einer internen Auflistung eines Objekts durch die Anwendung der Arraynotation auf das Objekt aufgerufen werden.|  
|Der Zugriff erfolgt über einen einfachen Namen.|Der Zugriff erfolgt über einen Index.|  
|Kann ein statischer Member oder ein Instanzmember sein.|Muss ein Instanzmember sein.|  
|Ein [get](../../language-reference/keywords/get.md)-Accessor einer Eigenschaft weist keine Parameter auf.|Ein `get`-Accessor eines Indexers hat dieselbe Liste formaler Parameter wie der Indexer.|  
|Ein [set](../../language-reference/keywords/set.md)-Accessor einer Eigenschaft enthält den impliziten `value`-Parameter.|Ein `set`-Accessor eines Indexers enthält neben dem [value](../../language-reference/keywords/value.md)-Parameter auch dieselbe Liste formaler Parameter wie der Indexer.|  
|Unterstützt Kurzsyntax mit [Auto-Implemented Properties (Automatisch implementierte Eigenschaften)](../classes-and-structs/auto-implemented-properties.md).|Unterstützt Ausdruckskörpermember für nur abrufende Indexer.|  
  
## <a name="see-also"></a>Siehe auch

- [C#-Programmierhandbuch](../index.md)
- [Indexer](./index.md)
- [Eigenschaften](../classes-and-structs/properties.md)
