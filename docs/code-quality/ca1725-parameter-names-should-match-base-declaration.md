---
title: "CA1725: Nazwy parametrów powinny pasować do podstawowej deklaracji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 0953e2c4f05e8ba01998893b2d790df832af3fef
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: Nazwy parametrów powinny pasować do podstawowej deklaracji
|||  
|-|-|  
|TypeName|ParameterNamesShouldMatchBaseDeclaration|  
|CheckId|CA1725|  
|Kategoria|Microsoft.Naming|  
|Zmiana kluczowa|Kluczowa|  
  
## <a name="cause"></a>Przyczyna  
 Nazwa parametru w widocznej zewnętrznie metodzie zastąpienia nie jest zgodna z nazwą parametru w deklaracji podstawowej metody lub nazwę parametru w deklaracji metody interfejsu.  
  
## <a name="rule-description"></a>Opis reguły  
 Spójne nazywanie parametrów w zastąpieniu hierarchii zwiększa użyteczność zastąpienia metody. Jeśli nazwa parametru w metodzie pochodnej różni się od nazwy podstawowej deklaracji, może nie być jasne, czy metoda jest zastąpieniem metody podstawowej, czy też nowym przeciążeniem metody.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Aby naprawić naruszenie tej reguły, Zmień nazwę parametru, aby pasować do podstawowej deklaracji. Poprawka jest istotne zmiany dla metod widoczne COM.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżenia od tej reguły, z wyjątkiem metod widoczne COM w bibliotekach, które wcześniej zostały dostarczone.