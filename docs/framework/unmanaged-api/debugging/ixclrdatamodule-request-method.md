---
title: IXCLRDataModule::Request-Methode
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7d04e5630bd196ef534f72a0c3924019315f3774
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632225"
---
# <a name="ixclrdatamodulerequest-method"></a>IXCLRDataModule::Request-Methode

Anforderungen zum Auffüllen mit Daten für das Modul des angegebenen Puffers.

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>Syntax

```cpp
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a>Parameter

`reqCode`\
[in] Der Anforderungstyp gesendet werden.

`inBufferSize`\
[in] die Größe des Eingabepuffers übergeben werden.

`inBuffer`\
[in, size_is(inBufferSize)] Zeiger auf den Puffer für die Rohdaten in der Anforderung gesendet werden.

`outBufferSize`\
[in] Die Größe des Ausgabepuffers.

`outBuffer`\
[Out, size_is(outBufferSize)] Zeiger auf den Puffer zum Speichern der Anforderungsantwort verwendet.

## <a name="remarks"></a>Hinweise

Die angegebene Methode ist Teil der `IXCLRDataModule` Schnittstelle, und mit dem der 36. Steckplatz der virtuellen Methodentabelle entspricht.

## <a name="requirements"></a>Anforderungen

**Plattformen:** Weitere Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).
**Header:** Keine **Bibliothek:** Keine **.NET Framework-Versionen:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>Siehe auch

- [Debuggen](index.md)
- [IXCLRDataModule-Schnittstelle](ixclrdatamodule-interface.md)
