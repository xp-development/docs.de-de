---
title: Implizit typisierte Lambdaausdrücke
description: Erfahren Sie, warum Sie keine implizit typisierte Variablendeklaration verwenden können, um einen Lambdaausdruck zu deklarieren.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: a3851da9-e018-4389-9922-233db7d0f841
ms.openlocfilehash: c6b0f2666a5c67ce8c89222da5959304ecb8fb93
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039125"
---
# <a name="implicitly-typed-lambda-expressions"></a>Implizit typisierte Lambdaausdrücke

Sie können keine implizit typisierte Variablendeklaration verwenden, um einen Lambdaausdruck zu deklarieren.
Dadurch entsteht ein zirkuläres logisches Problem für den Compiler. Die Deklaration `var` stellt den Compiler an, den Variablentyp aus dem Ausdruckstyp rechts vom Zuweisungsoperator abzuleiten. Ein Lambdaausdruck hat keinen Kompilierzeittyp, kann aber in jeden beliebigen passenden Delegats- oder Ausdruckstyp konvertiert werden. Wenn Sie einer Variablen eines Delegats- oder Ausdruckstyps einen Lambdaausdruck zuweisen, sagen Sie damit dem Compiler, dass er den Lambdaausdruck, wenn möglich, in einen Ausdruck oder Delegat konvertieren soll, der der Signatur der zugewiesenen Variablen entspricht. Der Compiler muss versuchen zu erreichen, dass das Objekt, das sich rechts von der Zuweisung befindet, mit dem Typen links von der Zuweisung übereinstimmt. 

Die Objekte, die sich jeweils neben dem Compiler befinden, dürfen dem Compiler nicht auftragen, sich das Objekt auf der jeweils anderen Seite des Zuweisungsoperators anzuschauen, um festzustellen, ob der Typ dieses Objekts mit dem jeweils anderen Objekt übereinstimmt.

Sie können Sich in [diesem Artikel](https://download.microsoft.com/download/5/4/B/54B83DFE-D7AA-4155-9687-B0CF58FF65D7/type-inference.pdf) darüber informieren, warum die C#-Programmiersprachen dieses Verhalten vorgibt (zum Download als PDF-Datei)
