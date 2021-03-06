---
title: ICorProfilerInfo2::GetContextStaticAddress-Methode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: d5d7da343148d5f1c2aa9b2b639b094f8269199b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433204"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a>ICorProfilerInfo2::GetContextStaticAddress-Methode
Ruft die Adresse für das angegebene Kontext statische Feld ab, das sich im Gültigkeitsbereich des angegebenen Kontexts befindet.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a>Parameter  
 `classId`  
 in Die ID der Klasse, die das angeforderte Kontext statische Feld enthält.  
  
 `fieldToken`  
 in Das Metadatentoken für das angeforderte Kontext statische Feld.  
  
 `contextId`  
 in Die ID des Kontexts, bei dem es sich um den Bereich für das angeforderte Kontext statische Feld handelt.  
  
 `ppAddress`  
 vorgenommen Ein Zeiger auf die Adresse des statischen Felds, das sich im angegebenen Kontext befindet.  
  
## <a name="remarks"></a>Hinweise  
 Die `GetContextStaticAddress`-Methode kann eine der folgenden Methoden zurückgeben:  
  
- Ein CORPROF_E_DATAINCOMPLETE HRESULT, wenn dem angegebenen statischen Feld keine Adresse im angegebenen Kontext zugewiesen wurde.  
  
- Die Adressen von Objekten, die sich möglicherweise im Garbage Collection Heap befinden. Diese Adressen können nach Garbage Collection ungültig werden. Daher sollten Profiler nach Garbage Collection nicht davon ausgehen, dass Sie gültig sind.  
  
 Bevor der Klassenkonstruktor einer Klasse abgeschlossen ist, gibt `GetContextStaticAddress` CORPROF_E_DATAINCOMPLETE für alle statischen Felder zurück, obwohl einige der statischen Felder möglicherweise bereits initialisiert sind und Garbage Collection Objekte rooting.  
  
## <a name="requirements"></a>Voraussetzungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [ICorProfilerInfo-Schnittstelle](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2-Schnittstelle](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
