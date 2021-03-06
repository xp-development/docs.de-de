---
title: 'Gewusst wie: Aufrufen von Windows-APIs'
ms.date: 07/20/2015
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
ms.openlocfilehash: 6f3c53243d7aeb73be81796d5ca185c3a3c41c72
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348704"
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Gewusst wie: Aufrufen von Windows-APIs (Visual Basic)
In diesem Beispiel wird die `MessageBox`-Funktion in User32. dll definiert und aufgerufen und dann eine Zeichenfolge an Sie weitergeleitet.  
  
## <a name="example"></a>Beispiel  
 [!code-vb[VbVbalrInterop#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
 Dieses Beispiel erfordert Folgendes:  
  
- Einen Verweis auf den <xref:System>-Namespace  
  
## <a name="robust-programming"></a>Robuste Programmierung  
 Die folgenden Bedingungen können einen Ausnahmefehler verursachen:  
  
- Die Methode ist nicht statisch, ist abstrakt oder wurde zuvor definiert. Der übergeordnete Typ ist eine Schnittstelle, oder die Länge von *Name* oder *dllName* ist 0 (null). (<xref:System.ArgumentException>)  
  
- Der *Name* oder der *dllName* ist `Nothing`. (<xref:System.ArgumentNullException>)  
  
- Der enthaltende Typ wurde zuvor mit `CreateType` erstellt. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Siehe auch

- [Genauere Betrachtung von Plattformaufrufen](../../../framework/interop/consuming-unmanaged-dll-functions.md#a-closer-look-at-platform-invoke)
- [Beispiele für Plattformaufrufe](../../../framework/interop/platform-invoke-examples.md)
- [Verwenden nicht verwalteter DLL-Funktionen](../../../framework/interop/consuming-unmanaged-dll-functions.md)
- [Definieren einer Methode mit Reflektionsausgabe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w63y4d4f(v=vs.100))
- [Exemplarische Vorgehensweise: Aufrufen von Windows-APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
- [COM-Interop](../../../visual-basic/programming-guide/com-interop/index.md)
