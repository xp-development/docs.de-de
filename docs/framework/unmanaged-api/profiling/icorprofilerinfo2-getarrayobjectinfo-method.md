---
title: ICorProfilerInfo2::GetArrayObjectInfo-Methode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
ms.openlocfilehash: 97b127c9a6aac0a0fefe25faf294791dcd2c8e41
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436029"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo-Methode
Ruft ausführliche Informationen zu einem Array Objekt ab.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a>Parameter  
 `objectId`  
 in Die ID eines gültigen Array Objekts.  
  
 `cDimensions`  
 in Der Rang (Anzahl der Dimensionen) des Arrays.  
  
 `pDimensionSizes`  
 vorgenommen Ein Array, das ganze Zahlen enthält, die jeweils die Größe einer Dimension des Arrays darstellen.  
  
 `pDimensionLowerBounds`  
 vorgenommen Ein Array, das ganze Zahlen enthält, die jeweils die untere Grenze einer Dimension des Arrays darstellen.  
  
 `ppData`  
 vorgenommen Ein Zeiger auf die Adresse des Rohdaten Puffers für das Array, das entsprechend der C++ Konvention angeordnet ist.  
  
## <a name="remarks"></a>Hinweise  
 Die `pDimensionSizes` und `pDimensionLowerBounds` sind parallele Arrays, sodass die Elemente, die sich am selben Index in jedem Array befinden, Merkmale derselben Entität sind.  
  
## <a name="requirements"></a>Voraussetzungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Bibliothek:** CorGuids.lib  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [ICorProfilerInfo-Schnittstelle](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2-Schnittstelle](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
