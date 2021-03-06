---
title: Spawnderivedclass-Funktion (Referenz zur nicht verwalteten API)
description: Die spawnderivedclass-Funktion erstellt ein neues-Objekt, das von einem-Objekt abgeleitet wird.
ms.date: 11/06/2017
api_name:
- SpawnDerivedClass
api_location:
- WMINet_Utils.dll
api_type:
- DLLExport
f1_keywords:
- SpawnDerivedClass
helpviewer_keywords:
- SpawnDerivedClass function [.NET WMI and performance counters]
topic_type:
- Reference
ms.openlocfilehash: f72e6b1c356077a94b141e40d6efe485e77e7a9e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120178"
---
# <a name="spawnderivedclass-function"></a>Spawnderivedclass-Funktion
Erstellt ein neu abgeleitetes Klassenobjekt aus einem angegebenen Objekt.    
  
[!INCLUDE[internalonly-unmanaged](../../../../includes/internalonly-unmanaged.md)]
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT SpawnDerivedClass (
   [in] int                  vFunc, 
   [in] IWbemClassObject*    ptr, 
   [in] LONG                 lFlags,
   [out] IWbemClassObject**  ppNewClass); 
```  

## <a name="parameters"></a>Parameter

`vFunc`  
in Dieser Parameter wird nicht verwendet.

`ptr`  
in Ein Zeiger auf eine [IWbemClassObject](/windows/desktop/api/wbemcli/nn-wbemcli-iwbemclassobject) -Instanz.

`lFlags`  
[in]: Reserviert Dieser Parameter muss 0 sein.

`ppNewClass`  
vorgenommen Empfängt den Zeiger auf das neue Klassen Definitions Objekt. Wenn ein Fehler auftritt, wird kein neues Objekt zurückgegeben, und `ppNewClass` bleibt unverändert. Der Wert kann nicht `null`werden.

## <a name="return-value"></a>Rückgabewert

Die folgenden Werte, die von dieser Funktion zurückgegeben werden, sind in der *wbemcli. h* -Header Datei definiert, oder Sie können Sie als Konstanten im Code definieren:

|Konstante  |Wert  |Beschreibung  |
|---------|---------|---------|
| `WBEM_E_FAILED` | 0x80041001 | Es ist ein allgemeiner Fehler aufgetreten. |
| `WBEM_E_INVALID_OPERATION` | 0x80041016 | Es wurde ein ungültiger Vorgang angefordert, z. b. das Erzeugen einer Klasse aus einer Instanz. |
| `WBEM_E_INCOMPLETE_CLASS` | Die Quell Klasse wurde nicht vollständig definiert oder bei der Windows-Verwaltung registriert, sodass eine neue abgeleitete Klasse nicht zulässig ist. |
| `WBEM_E_OUT_OF_MEMORY` | 0x80041006 | Es ist nicht genügend Arbeitsspeicher verfügbar, um den Vorgang abzuschließen. |
| `WBEM_E_INVALID_PARAMETER` | 0x80041008 | `ppNewClass` ist `null`. |
| `WBEM_S_NO_ERROR` | 0 | Der Funktions Aufrufvorgang war erfolgreich.  |
  
## <a name="remarks"></a>Hinweise

Diese Funktion umschließt einen aufrufsbefehl an die [IWbemClassObject:: spawnderivedclass](/windows/desktop/api/wbemcli/nf-wbemcli-iwbemclassobject-clone) -Methode.

`ptr` muss eine Klassendefinition sein, die zur übergeordneten Klasse des erzeugten Objekts wird. Das zurückgegebene-Objekt wird zu einer Unterklasse des aktuellen-Objekts.

Das neue-Objekt, das in `ppNewClass` zurückgegeben wird, wird automatisch zu einer Unterklasse des aktuellen-Objekts. Dieses Verhalten kann nicht überschrieben werden. Es gibt keine andere Methode, mit der Unterklassen (abgeleitete Klassen) erstellt werden können.

## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../get-started/system-requirements.md).  
  
 **Header:** WMINet_Utils. idl  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  
  
## <a name="see-also"></a>Siehe auch

- [WMI und Leistungsindikatoren (Referenz zur nicht verwalteten API)](index.md)
