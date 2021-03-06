---
title: _CorValidateImage-Funktion
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
ms.openlocfilehash: 42da5bb761ba8ce388bd41d46e8fdc4561ad0290
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136882"
---
# <a name="_corvalidateimage-function"></a>_CorValidateImage-Funktion
Überprüft Images des verwalteten Moduls, und benachrichtigt das Betriebssystemladeprogramm, nachdem sie geladen wurden.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a>Parameter  
 `ImageBase`  
 in Ein Zeiger auf die Startposition des Bilds, das als verwalteter Code validiert werden soll. Das Image muss bereits in den Arbeitsspeicher geladen werden.  
  
 `FileName`  
 in Der Dateiname des Bilds.  
  
## <a name="return-value"></a>Rückgabewert  
 Diese Funktion gibt die Standardwerte `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`und `E_FAIL`sowie die folgenden Werte zurück.  
  
|Rückgabewert|Beschreibung|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|Das Bild ist ungültig. Dieser Wert weist das HRESULT 0xC000007BL auf.|  
|`STATUS_SUCCESS`|Das Bild ist gültig. Dieser Wert hat das HRESULT 0x00000000L.|  
  
## <a name="remarks"></a>Hinweise  
 In Windows XP und höheren Versionen überprüft das Betriebssystem-Lade Modul die verwalteten Module, indem er das com-deskriptorverzeichnisbit im COFF-Header (Common Object File Format) untersucht. Ein festgelegtes Bit gibt ein verwaltetes Modul an. Wenn das Lade Modul ein verwaltetes Modul erkennt, lädt es Mscoree. dll und ruft `_CorValidateImage`auf, das die folgenden Aktionen ausführt:  
  
- Bestätigt, dass das Image ein gültiges verwaltetes Modul ist.  
  
- Ändert den Einstiegspunkt im Bild in einen Einstiegspunkt in der Common Language Runtime (CLR).  
  
- Bei 64-Bit-Versionen von Windows ändert das Bild, das sich im Arbeitsspeicher befindet, indem es von das Format PE32 in das Format PE32 + Format transformiert wird.  
  
- Kehrt zum Lade Modul zurück, wenn die Images des verwalteten Moduls geladen werden.  
  
 Bei ausführbaren Images Ruft das Betriebssystem-Lade Programm dann die [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) -Funktion auf, unabhängig vom Einstiegspunkt, der in der ausführbaren Datei angegeben ist. Bei dll-assemblyimages Ruft das Lade Modul die [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) -Funktion auf.  
  
 `_CorExeMain` oder `_CorDllMain` führt die folgenden Aktionen aus:  
  
- Initialisiert die CLR.  
  
- Der verwaltete Einstiegspunkt wird aus dem CLR-Header der Assembly lokalisiert.  
  
- Startet die Ausführung.  
  
 Das Lade Modul ruft die [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) -Funktion auf, wenn verwaltete Modul Images entladen werden. Diese Funktion führt jedoch keine Aktion aus. Er gibt nur zurück.  
  
## <a name="requirements"></a>Anforderungen  
 **Plattformen:** Informationen finden Sie unter [Systemanforderungen](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor. h  
  
 **Bibliothek:** Als Ressource in Mscoree. dll enthalten  
  
 **.NET Framework-Versionen:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Siehe auch

- [Globale statische Metadatenfunktionen](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
