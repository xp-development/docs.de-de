---
title: LoggingLevelEnum-Enumeration
ms.date: 03/30/2017
api_name:
- LoggingLevelEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- LoggingLevelEnum
helpviewer_keywords:
- LoggingLevelEnum enumeration [.NET Framework debugging]
ms.assetid: 09daac08-005a-46b2-beab-408d0820c5e5
topic_type:
- apiref
ms.openlocfilehash: 01e1eafd9955a0876f77e34eb73c2a3fc6d815c2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139202"
---
# <a name="logginglevelenum-enumeration"></a>LoggingLevelEnum-Enumeration
Gibt den Schweregrad einer beschreibenden Meldung an, die in das Ereignisprotokoll geschrieben wird, wenn ein verwalteter Thread ein Ereignis protokolliert.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
typedef enum LoggingLevelEnum {  
    LTraceLevel0 = 0,  
    LTraceLevel1,  
    LTraceLevel2,  
    LTraceLevel3,  
    LTraceLevel4,  
    LStatusLevel0 = 20,  
    LStatusLevel1,  
    LStatusLevel2,  
    LStatusLevel3,  
    LStatusLevel4,  
    LWarningLevel = 40,  
    LErrorLevel = 50,  
    LPanicLevel = 100  
} LoggingLevelEnum;  
```  
  
## <a name="members"></a>Member  
  
|Member|Beschreibung|  
|------------|-----------------|  
|`LTraceLevel0`|Die Meldung ist eine Ablauf Verfolgungs Ebene von 0.|  
|`LTraceLevel1`|Die Meldung ist eine Ablauf Verfolgungs Ebene 1.|  
|`LTraceLevel2`|Die Meldung ist eine Ablauf Verfolgungs Ebene 2.|  
|`LTraceLevel3`|Die Meldung ist eine Ablauf Verfolgungs Ebene 3.|  
|`LTraceLevel4`|Die Meldung ist eine Ablauf Verfolgungs Ebene 4.|  
|`LStatusLevel0`|Die Meldung ist eine Status Ebene von 0.|  
|`LStatusLevel1`|Die Meldung ist eine Status Ebene 1.|  
|`LStatusLevel2`|Die Meldung ist eine Status Ebene 2.|  
|`LStatusLevel3`|Die Meldung ist eine Status Ebene 3.|  
|`LStatusLevel4`|Die Meldung ist eine Status Ebene 4.|  
|`LWarningLevel`|Die Meldung ist eine Warnstufe.|  
|`LErrorLevel`|Die Meldung ist eine Fehler Ebene.|  
|`LPanicLevel`|Die Meldung ist eine Panik Ebene.|  
  
## <a name="remarks"></a>Hinweise  
 Der Common Language Runtime (CLR) Ruft die [ICorDebugManagedCallback:: LogMessage](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-logmessage-method.md) -Methode auf, um den Debugger zu benachrichtigen, dass ein verwalteter Thread ein Ereignis protokolliert hat. Die CLR übergibt einen Wert der `LoggingLevelEnum`-Enumeration, um den Schweregrad der Meldung anzugeben, die der verwaltete Thread in das Ereignisprotokoll geschrieben hat.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- <xref:System.Diagnostics.EventLog>
- [Debuggen von Enumerationen](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
