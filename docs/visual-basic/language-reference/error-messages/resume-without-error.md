---
title: Ohne Fehler fortsetzen.
ms.date: 07/20/2015
f1_keywords:
- vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
ms.openlocfilehash: 61332486b20af66af24eac06b222a38353578c16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055159"
---
# <a name="resume-without-error"></a>Ohne Fehler fortsetzen.
Ein `Resume` Anweisung außerhalb der Fehlerbehandlungscode aufgetreten oder der Code erfolgte ein Sprung in einen Fehlerhandler, obwohl kein Fehler vorliegt.  
  
## <a name="to-correct-this-error"></a>So beheben Sie diesen Fehler  
  
1. Verschieben der `Resume` -Anweisung in einen Fehlerhandler für, oder löschen.  
  
2. Suchen Sie springen zu Bezeichnungen können nicht über Prozeduren auftreten, also das Verfahren für die Bezeichnung, die den Fehlerhandler identifiziert. Wenn Sie feststellen, dass eine doppelte Bezeichnung, die als Ziel angegebene eine `GoTo` Anweisung, die kein `On Error GoTo` -Anweisung, die zeilenbezeichnung mit ihr vorgesehenes Ziel ich stimme zu ändern.  
  
## <a name="see-also"></a>Siehe auch

- [Resume-Anweisung](../../../visual-basic/language-reference/statements/resume-statement.md)
- [On Error-Anweisung](../../../visual-basic/language-reference/statements/on-error-statement.md)
