---
title: <forcePerformanceCounterUniqueSharedMemoryReads>-Element
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: efa6dce1035f7d2cf63b74c6a03d911b5dede722
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73116950"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forceperformancecounteruniquesharedmemoryreads > Element
Gibt an, ob „PerfCounter.dll“ die Registrierungseinstellung „CategoryOptions“ in einer .NET Framework Version 1.1-Anwendung verwendet, um zu bestimmen, ob Leistungsindikatordaten aus kategoriespezifischem, gemeinsam genutztem Arbeitsspeicher oder aus dem globalen Arbeitsspeicher geladen werden.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) \
&nbsp;&nbsp;&nbsp;&nbsp; **\<forceperformancecounteruniquesharedmemoryreads >**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`enabled`|Erforderliches Attribut.<br /><br /> Gibt an, ob PerfCounter. dll die categoryoptions-Registrierungs Einstellung verwendet, um zu bestimmen, ob Leistungsdaten aus dem kategoriespezifischen freigegebenen oder globalen Arbeitsspeicher geladen werden sollen.|  
  
## <a name="enabled-attribute"></a>Enabled-Attribut  
  
|Wert|Beschreibung|  
|-----------|-----------------|  
|`false`|PerfCounter. dll verwendet nicht die Registrierungs Einstellung categoryoptions, dies ist die Standardeinstellung.|  
|`true`|PerfCounter. dll verwendet die Registrierungs Einstellung categoryoptions.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|`configuration`|Das Stammelement in jeder von den Common Language Runtime- und .NET Framework-Anwendungen verwendeten Konfigurationsdatei.|  
|`runtime`|Enthält Informationen über die Assemblybindung und die Garbage Collection.|  
  
## <a name="remarks"></a>Hinweise  
 In Versionen der .NET Framework vor dem .NET Framework 4 entsprach die Version von PerfCounter. dll, die geladen wurde, der Laufzeit, die in den Prozess geladen wurde. Wenn auf einem Computer sowohl der .NET Framework Version 1,1 als auch der .NET Framework 2,0 installiert war, würde eine .NET Framework 1,1-Anwendung die .NET Framework Version 1,1 von PerfCounter. dll laden. Beginnend mit dem .NET Framework 4 wird die neueste installierte Version von "PerfCounter. dll" geladen. Dies bedeutet, dass eine .NET Framework 1,1-Anwendung die .NET Framework 4-Version von "PerfCounter. dll" lädt, wenn die .NET Framework 4 auf dem Computer installiert ist.  
  
 Beginnend mit dem .NET Framework 4 überprüft PerfCounter. dll bei der Nutzung von Leistungsindikatoren den Registrierungs Eintrag categoryoptions für jeden Anbieter, um zu bestimmen, ob er aus dem kategoriespezifischen freigegebenen Arbeitsspeicher oder dem globalen gemeinsam genutzten Speicher lesen soll. Der .NET Framework 1,1 PerfCounter. dll liest diesen Registrierungs Eintrag nicht, da er keinen kategoriespezifischen freigegebenen Arbeitsspeicher kennt. Er liest immer aus dem globalen gemeinsam genutzten Speicher.  
  
 Aus Gründen der Abwärtskompatibilität überprüft das .NET Framework 4 PerfCounter. dll den Registrierungs Eintrag categoryoptions nicht, wenn er in einer .NET Framework 1,1-Anwendung ausgeführt wird. Es verwendet einfach den globalen gemeinsam genutzten Speicher, genau wie die .NET Framework 1,1 PerfCounter. dll. Sie können jedoch die .NET Framework 4 PerfCounter. dll anweisen, die Registrierungs Einstellung zu überprüfen, indem Sie das `<forcePerformanceCounterUniqueSharedMemoryReads>`-Element aktivieren.  
  
> [!NOTE]
> Das Aktivieren des `<forcePerformanceCounterUniqueSharedMemoryReads>`-Elements garantiert nicht, dass kategoriespezifischer gemeinsam genutzter Arbeitsspeicher verwendet wird. Wenn die Einstellung auf `true` aktiviert ist, verweist PerfCounter. dll nur auf die Registrierungs Einstellung categoryoptions. Die Standardeinstellung für categoryoptions ist die Verwendung des kategoriespezifischen freigegebenen Speichers. Sie können jedoch categoryoptions ändern, um anzugeben, dass der globale gemeinsame Arbeitsspeicher verwendet werden soll.  
  
 Der Registrierungsschlüssel, der die Einstellung categoryoptions enthält, ist HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\< CategoryName\>\Performance. Standardmäßig ist "categoryoptions" auf "3" festgelegt, was PerfCounter. dll anweist, kategoriespezifischen freigegebenen Arbeitsspeicher zu verwenden. Wenn categoryoptions auf 0 festgelegt ist, verwendet PerfCounter. dll globalen gemeinsam genutzten Arbeitsspeicher. Instanzdaten werden nur dann wieder verwendet, wenn der Name der Instanz, die erstellt wird, mit der Instanz identisch ist, die wieder verwendet wird. Alle Versionen können in die Kategorie schreiben. Wenn categoryoptions auf 1 festgelegt ist, wird der globale freigegebene Speicher verwendet, aber Instanzdaten können wieder verwendet werden, wenn der Kategoriename dieselbe Länge wie die wiederverwendbare Kategorie hat.  
  
 Die Einstellungen 0 und 1 können zu Speicher Verlusten und zum Auffüllen des Leistungs Zählers führen.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird gezeigt, wie Sie angeben können, dass "PerfCounter. dll" auf den Registrierungs Eintrag "categoryoptions" verweisen soll, um zu bestimmen, ob der kategorisierte Speicher verwendet werden soll.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Siehe auch

- [Schema für Laufzeiteinstellungen](index.md)
- [Konfigurationsdateischema](../index.md)
