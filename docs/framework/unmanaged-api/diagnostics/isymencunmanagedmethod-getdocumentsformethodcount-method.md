---
title: ISymENCUnmanagedMethod::GetDocumentsForMethodCount-Methode
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
ms.openlocfilehash: 057b901337ded7b5336ef673624d8d6c827c8932
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448671"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a>ISymENCUnmanagedMethod::GetDocumentsForMethodCount-Methode
Ruft die Anzahl der Dokumente ab, in denen diese Methode Zeilen aufweist.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a>Parameter  
 `pRetVal`  
 vorgenommen Ein Zeiger auf einen `ULONG32`, der die Größe des Puffers empfängt, der zum enthalten der Dokumente erforderlich ist.  
  
## <a name="return-value"></a>Rückgabewert  
 S_OK, wenn die Methode erfolgreich ist. andernfalls E_FAIL oder ein anderer Fehlercode.  
  
## <a name="requirements"></a>Voraussetzungen  
 **Header:** Corsym. idl, corsym. h  
  
## <a name="see-also"></a>Siehe auch

- [ISymENCUnmanagedMethod-Schnittstelle](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
