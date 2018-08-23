---
title: 'CA1722: Identyfikatory nie powinny mieć niepoprawnego prefiksu | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6e218f4c9abb86fb5115a1df4fb6f66bb1856e16
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42678637"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Identyfikatory powinny mieć poprawny prefiks
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Najnowszą wersję tego tematu znajduje się w temacie [CA1722: identyfikatory nie powinny mieć niepoprawnego prefiksu](https://docs.microsoft.com/visualstudio/code-quality/ca1722-identifiers-should-not-have-incorrect-prefix).  
  
Element TypeName | IdentifiersShouldNotHaveIncorrectPrefix |  
| CheckId | CA1722 |  
| Kategoria | Microsoft.Naming|  
| Zmiana powodująca niezgodność | Przerwanie |  
  
## <a name="cause"></a>Przyczyna  
 Identyfikator ma niepoprawny prefiks.  
  
## <a name="rule-description"></a>Opis reguły  
 Zgodnie z konwencją, tylko niektóre elementy programowania mają nazwy rozpoczynające się od określonego prefiksu.  
  
 Nazwy typów nie ma określonego prefiksu i nie powinien być poprzedzony "C". Ta zasada zgłasza naruszenia nazwy typów, takich jak "CMyClass" i nie raportuje naruszenia nazwy typów, takich jak "Pamięci podręcznej".  
  
 Konwencje nazewnictwa Obejmij wygląd wspólnych bibliotek obiektu docelowego środowiska uruchomieniowego języka wspólnego. Zmniejsza to nauki, jest wymagany dla nowe biblioteki oprogramowania, która zwiększa poziom zaufania klientów, że biblioteka został opracowany przez osobę, która ma doświadczenie w tworzenie kodu zarządzanego.  
  
## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia  
 Usuń prefiks z identyfikatorem.  
  
## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia  
 Nie pomijaj ostrzeżeń dla tej reguły.  
  
## <a name="related-rules"></a>Powiązane reguły  
 [CA1715: Identyfikatory powinny mieć poprawny prefiks](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)



