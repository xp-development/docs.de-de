---
title: ICorDebugThread2::GetConnectionID-Methode
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetConnectionID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetConnectionID
helpviewer_keywords:
- ICorDebugThread2::GetConnectionID method [.NET Framework debugging]
- GetConnectionID method [.NET Framework debugging]
ms.assetid: 9c76b587-f941-4fa1-8b86-f3494fb10c8e
topic_type:
- apiref
ms.openlocfilehash: a81842132769934a6f5f34e6dc462bba77b3854a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138689"
---
# <a name="icordebugthread2getconnectionid-method"></a>ICorDebugThread2::GetConnectionID-Methode
Ruft den Verbindungs Bezeichner für dieses ICorDebugThread2-Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetConnectionID (  
    [out] CONNID *pdwConnectionId  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `pdwConnectionId`  
 vorgenommen Ein-`CONNID`, der den Verbindungs Bezeichner darstellt.  
  
## <a name="remarks"></a>Hinweise  
 Die `GetConnectionID`-Methode gibt 0 (null) im `pdwConnectionId`-Parameter zurück, wenn dieser Thread nicht Teil einer Verbindung ist.  
  
 Wenn dieser Thread mit einer Instanz von Microsoft SQL Server 2005 Analysis Services (SSAS) verbunden ist, wird die `CONNID` einem Server Prozess Bezeichner (SPID) zugeordnet.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorDebug.idl, CorDebug.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
