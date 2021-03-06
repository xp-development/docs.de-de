---
title: 'Gewusst wie: Suchen der festgelegten Differenz zwischen zwei Listen (LINQ)'
ms.date: 07/20/2015
ms.assetid: b5b25474-10a8-4df6-aab5-75621bb6b68e
ms.openlocfilehash: cd33c08416cce5afb6cf7507335f753160b8c6ff
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344587"
---
# <a name="how-to-find-the-set-difference-between-two-lists-linq-visual-basic"></a>Gewusst wie: Suchen der festgelegten Differenz zwischen zwei Listen (LINQ) (Visual Basic)
In diesem Beispiel wird veranschaulicht, wie Sie mit LINQ zwei Listen mit Zeichenfolgen vergleichen und die Zeilen ausgeben, die in names1.txt, aber nicht in names2.txt enthalten sind.  
  
### <a name="to-create-the-data-files"></a>So erstellen Sie die Datendateien  
  
1. Kopieren Sie names1. txt und names2. txt in ihren Projektmappenordner, wie in Gewusst [wie: kombinieren und Vergleichen von Zeichen folgen Auflistungen (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-combine-and-compare-string-collections-linq.md)gezeigt.  
  
## <a name="example"></a>Beispiel  
  
```vb  
Class CompareLists  
  
    Shared Sub Main()  
  
        ' Create the IEnumerable data sources.  
        Dim names1 As String() = System.IO.File.ReadAllLines("../../../names1.txt")  
        Dim names2 As String() = System.IO.File.ReadAllLines("../../../names2.txt")  
  
        ' Create the query. Note that method syntax must be used here.  
        Dim differenceQuery = names1.Except(names2)  
        Console.WriteLine("The following lines are in names1.txt but not names2.txt")  
  
        ' Execute the query.  
        For Each name As String In differenceQuery  
            Console.WriteLine(name)  
        Next  
  
        ' Keep console window open in debug mode.  
        Console.WriteLine("Press any key to exit.")  
        Console.ReadKey()  
    End Sub  
End Class  
' Output:  
' The following lines are in names1.txt but not names2.txt  
' Potra, Cristina  
' Noriega, Fabricio  
' Aw, Kam Foo  
' Toyoshima, Tim  
' Guy, Wey Yuan  
' Garcia, Debra  
```  
  
 Einige Typen von Abfrage Vorgängen in Visual Basic, z. b. <xref:System.Linq.Enumerable.Except%2A>, <xref:System.Linq.Enumerable.Distinct%2A>, <xref:System.Linq.Enumerable.Union%2A>und <xref:System.Linq.Enumerable.Concat%2A>, können nur in Methoden basierter Syntax ausgedrückt werden.  
  
## <a name="compiling-the-code"></a>Kompilieren des Codes  
Erstellen Sie ein Konsolen Anwendungsprojekt in VB.net mit einer `Imports`-Anweisung für den System. Linq-Namespace.
  
## <a name="see-also"></a>Siehe auch

- [LINQ und Zeichen folgen (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
