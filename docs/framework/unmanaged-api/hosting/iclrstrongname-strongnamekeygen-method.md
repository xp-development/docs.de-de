---
title: ICLRStrongName::StrongNameKeyGen-Methode
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: 4f3574e282d24fa11ffa2f85463f682c42098ae7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135050"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>ICLRStrongName::StrongNameKeyGen-Methode
Erstellt ein neues öffentliches/privates Schlüsselpaar für die Verwendung starker Namen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `wszKeyContainer`  
 in Der angeforderte Schlüssel Container Name. `wszKeyContainer` müssen entweder eine nicht leere Zeichenfolge oder NULL sein, um einen temporären Namen zu generieren.  
  
 `dwFlags`  
 in Ein-Wert, der angibt, ob der Schlüssel registriert bleiben soll. Die folgenden Werte werden unterstützt:  
  
- 0x00000000-wird verwendet, wenn `wszKeyContainer` NULL ist, um einen temporären Schlüssel Container Namen zu generieren.  
  
- 0x00000001 (`SN_LEAVE_KEY`): gibt an, dass der Schlüssel registriert bleiben soll.  
  
 `ppbKeyBlob`  
 vorgenommen Das zurückgegebene Paar aus öffentlichem und privatem Schlüssel.  
  
 `pcbKeyBlob`  
 vorgenommen Die Größe `ppbKeyBlob`in Byte.  
  
## <a name="return-value"></a>Rückgabewert  
 `S_OK`, wenn die Methode erfolgreich abgeschlossen wurde. andernfalls ein HRESULT-Wert, der einen Fehler angibt (siehe [Allgemeine HRESULT-Werte](https://go.microsoft.com/fwlink/?LinkId=213878) für eine Liste).  
  
## <a name="remarks"></a>Hinweise  
 Die [ICLRStrongName:: StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md) -Methode erstellt einen 1024-Bit-Schlüssel. Nachdem der Schlüssel abgerufen wurde, sollten Sie die [ICLRStrongName:: strongnamefrebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md) -Methode abrufen, um den zugewiesenen Speicher freizugeben.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** MetaHost. h  
  
 **Bibliothek:** Als Ressource in Mscoree. dll enthalten  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [StrongNameKeyGenEx-Methode](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName-Schnittstelle](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
