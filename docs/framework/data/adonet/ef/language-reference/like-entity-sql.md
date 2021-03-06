---
title: LIKE (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 8300e6d2-875b-481e-9ef4-e1e7c12d46fa
ms.openlocfilehash: f9e33c78235f637e0aa0622d9d8cc30255722beb
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319672"
---
# <a name="like-entity-sql"></a>LIKE (Entity SQL)
Ermittelt, ob ein bestimmter Zeichen-`String` mit einem angegebenen Muster übereinstimmt.  
  
## <a name="syntax"></a>Syntax  
  
```sql  
match [NOT] LIKE pattern [ESCAPE escape]  
```  
  
## <a name="arguments"></a>Argumente  
 `match`  
 Ein [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Ausdruck, der zu einem `String` ausgewertet wird.  
  
 `pattern`  
 Ein Muster, das mit dem angegebenen `String` verglichen werden soll.  
  
 `escape`  
 Ein Escapezeichen.  
  
 NICHT  
 Legt fest, dass das Ergebnis von LIKE negiert werden soll.  
  
## <a name="return-value"></a>Rückgabewert  
 `true`, wenn `string` mit dem Muster übereinstimmt, andernfalls `false`.  
  
## <a name="remarks"></a>Hinweise  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Ausdrücke, die den Like-Operator verwenden, werden auf die gleiche Weise ausgewertet wie Ausdrücke, die Gleichheit als Filterkriterien verwenden. @No__t_0 Ausdrücke, die den Like-Operator verwenden, können jedoch sowohl Literale als auch Platzhalter Zeichen enthalten.  
  
 In der folgenden Tabelle wird die Syntax des als Muster verwendeten `string` beschrieben.  
  
|Platzhalterzeichen|Beschreibung|Beispiel|  
|------------------------|-----------------|-------------|  
|%|Jeder `string` mit null oder mehr Zeichen.|`title like '%computer%'` findet alle Titel mit dem Wort `"computer"` an beliebiger Stelle im Titel.|  
|_ (Unterstrich)|Ein beliebiges einzelnes Zeichen.|`firstname like '_ean'` findet alle aus vier Buchstaben bestehenden Vornamen, die mit `"ean` enden, z. b. "Dean" oder "Sean".|  
|[ ]|Beliebiges einzelnes Zeichen im angegebenen Bereich ([a-f]) oder in der angegebenen Menge ([abcdef]).|`lastname like '[C-P]arsen'` sucht nach Nachnamen, die mit "Arsen" enden und mit einem beliebigen einzelnen Zeichen zwischen C und P beginnen, wie z. b. Carsen oder Larsen.|  
|[^]|Beliebiges einzelnes Zeichen, das nicht im angegebenen Bereich ([^a-f]) oder der angegebenen Menge ([^abcdef]) liegt.|`lastname like 'de[^l]%'` ermittelt alle Nachnamen, die mit "de" beginnen, und schließt "l" nicht als folgenden Buchstaben ein.|  
  
> [!NOTE]
> Der LIKE-Operator und die ESCAPE-Klausel von [!INCLUDE[esql](../../../../../../includes/esql-md.md)] können nicht auf `System.DateTime`-Werte oder `System.Guid`-Werte angewendet werden.  
  
 LIKE unterstützt Mustervergleiche im ASCII- und Unicode-Format. Wenn alle Parameter ASCII-Zeichen sind, wird ein ASCII-Mustervergleich ausgeführt. Wenn eines oder mehrere der Argumente von einem Unicode-Datentyp sind, werden alle Argumente in Unicode konvertiert, und ein Unicode-Mustervergleich wird durchgeführt. Bei der Verwendung von Unicode mit dem LIKE-Operator werden nachfolgende Leerzeichen berücksichtigt. Wird nicht der Typ Unicode verwendet, werden nachfolgende Leerzeichen ignoriert. Die Syntax der Muster Zeichenfolge von [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ist identisch mit der Syntax von Transact-SQL.  
  
 Zu einem Muster können normale Zeichen und Platzhalter gehören. Bei einem Mustervergleich müssen normale Zeichen exakt mit den im `string` angegebenen Zeichen übereinstimmen. Platzhalterzeichen können mit beliebigen Teilen der Zeichenfolge übereinstimmen. Wenn der LIKE-Operator mit Platzhalterzeichen verwendet wird, ist er flexibler als die Zeichenfolgen-Vergleichsoperatoren „=“ und „!=“.  
  
> [!NOTE]
> Bei Abfragen für einen bestimmten Anbieter können anbieterspezifische Erweiterungen verwendet werden. Solche Konstrukte können jedoch von anderen Anbietern anders behandelt werden. SqlServer unterstützt beispielsweise Muster der Form [erstes Zeichen-letztes Zeichen] und [^erstes Zeichen-letztes Zeichen], wobei die erste Form mit genau einem Zeichen zwischen "erstes Zeichen" und "letztes Zeichen" und die zweite Form mit genau einem Zeichen, das nicht zwischen "erstes Zeichen" und "letztes Zeichen" liegt, übereinstimmt.  
  
### <a name="escape"></a>Escape  
 Mithilfe der ESCAPE-Klausel kann nach Zeichenfolgen gesucht werden, die einen oder mehrere der im vorherigen Abschnitt beschriebenen speziellen Platzhalterzeichen enthalten. Nehmen Sie z. B. an, dass im Titel mehrerer Dokumente das Literal "100%" enthalten ist und Sie diese Dokumente finden möchten. Da der Prozentsatz (%) das Zeichen ist ein Platzhalter Zeichen, das Sie mit der [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Escape-Klausel versehen müssen, um die Suche erfolgreich auszuführen. Im Folgenden sehen Sie ein Beispiel für diesen Filter.  
  
```sql  
"title like '%100!%%' escape '!'"  
```  
  
 In diesem Suchausdruck wird das Platzhalterzeichen "%", das unmittelbar auf das Ausrufezeichen (!) folgt, als Literal und nicht als Platzhalterzeichen behandelt. Sie können ein beliebiges Zeichen als Escapezeichen verwenden, mit Ausnahme der [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Platzhalter Zeichen und der eckigen Klammer (`[ ]`). Im vorherigen Beispiel wird das Ausrufezeichen (!) als Escapezeichen verwendet.  
  
## <a name="example"></a>Beispiel  
 Die folgenden zwei [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Abfragen verwenden die like-und Escape-Operatoren, um zu bestimmen, ob eine bestimmte Zeichenfolge mit einem angegebenen Muster übereinstimmt. Die erste Abfrage sucht nach der `Name`, die mit den Zeichen `Down_` beginnt. In dieser Abfrage wird die ESCAPE-Option verwendet, da der Unterstrich (`_`) ein Platzhalterzeichen ist. Ohne Angeben der ESCAPE`Name`-Option würde die Abfrage alle `Down`-Werte zurückgeben, die mit dem Wort  beginnen, gefolgt von einem einzelnen Zeichen, das kein Unterstrich ist. Die Abfragen basieren auf dem AdventureWorks Sales-Modell. Führen Sie folgende Schritte aus, um diese Abfrage zu kompilieren und auszuführen:  
  
1. Befolgen Sie das Verfahren in [How an: Führen Sie eine Abfrage aus, die PrimitiveType-Ergebnisse zurückgibt ](../how-to-execute-a-query-that-returns-primitivetype-results.md).  
  
2. Übergeben Sie die folgende Abfrage als Argument an die `ExecutePrimitiveTypeQuery` -Methode:  
  
 [!code-sql[DP EntityServices Concepts#LIKE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#like)]  
  
## <a name="see-also"></a>Siehe auch

- [Entity SQL-Referenz](entity-sql-reference.md)
